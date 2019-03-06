---
title: CLR プロファイラと Windows ストア アプリ
ms.date: 03/30/2017
dev_langs:
- csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93344e1c5aa62e86d29a0110a9d8cffc3cea66ff
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358549"
---
# <a name="clr-profilers-and-windows-store-apps"></a>CLR プロファイラと Windows ストア アプリ

このトピックでは、分析に書き込み診断ツールが Windows ストア アプリ内で実行されているコードを管理するときに考慮する必要がありますについて説明します。 Windows ストア アプリに対して実行するときの作業を継続するために、既存の開発ツールを変更するためのガイドラインも提供します。 この情報を理解するには、ことをお勧めする診断ツールを変更する場合、ツール、Windows デスクトップ アプリケーションに対して正しく実行、対象となるようになりましたことで、この API を既に使用して共通言語ランタイム プロファイル API を使い慣れている場合、Windows ストア アプリに対して正しく実行します。

## <a name="introduction"></a>はじめに

過去の導入の段落で作成した場合、CLR のプロファイル API を使い慣れています。 管理対象のデスクトップ アプリケーションに対して適切に動作する診断ツールを既に作成しました。 これで、興味がある、ツールは、管理対象の Windows ストア アプリで動作するように対処します。 おそらく、この作業を行うし、簡単な作業ではないことが検出するこれ既に行ったします。 実際には、すべてのツール開発者にとって明らかなことができない可能性がある注意事項があります。 例:

- Windows ストア アプリは、権限が制限された重大なコンテキストで実行します。

- Windows メタデータ ファイルには、従来のマネージ モジュールと比較した場合、一意の特性があります。

- Windows ストア アプリでは、対話機能がダウンしたときにそれ自体を中断する習慣があります。

- プロセス間通信メカニズムは、さまざまな理由で機能しない可能性があります。

このトピックでは、注意する必要があるものとそれらに適切に対処する方法を示します。

CLR のプロファイル API に慣れていない場合より基本的な情報を検索するリソースをこのトピックの最後までスキップします。

特定の Windows Api と、使用方法の詳細を提供することは、このトピックの範囲外もです。 このトピックで、開始点を考慮し、ここで参照されているすべての Windows Api の詳細については、MSDN を参照してください。

## <a name="architecture-and-terminology"></a>アーキテクチャと用語

通常、診断ツールはの次の図に示すようなアーキテクチャです。 「プロファイラー、」という用語を使用しますが、このような多くのツールには、標準的なパフォーマンスまたはメモリのプロファイルのコード カバレッジなどの領域よりはるかに優れたモック オブジェクト フレームワーク、タイム トラベルのデバッグ、監視、そのためにアプリケーションが参照してください。 わかりやすくするためは、このトピックでは引き続きしてプロファイラーとしてこれらすべてのツールを参照してください。

このトピックでは、次の用語が使用されます。

**アプリケーション**

これは、プロファイラーが分析されているアプリケーションです。 通常、このアプリケーションの開発者は、アプリケーションの問題の診断に役立つ、プロファイラーを使用するがようになりました。 これまでは、このアプリケーションは、Windows デスクトップ アプリケーションになりますが、このトピックでは、Windows ストア アプリに求めています。

**Profiler DLL**

これは、分析対象のアプリケーションのプロセス領域に読み込まれるコンポーネントです。 このコンポーネントは、プロファイラーの「エージェント」とも呼ばれる実装、 [ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)(2、3 など) インターフェイスし、消費、 [ICorProfilerInfo](icorprofilerinfo-interface.md)(2、3 など) と可能性のある分析対象のアプリケーションに関するデータを収集するインターフェイスは、アプリケーションの動作の側面を変更します。

**Profiler の UI**

これは、profiler のユーザーと対話するデスクトップ アプリケーションです。 ユーザーにアプリケーションの状態を表示して、分析対象のアプリケーションの動作を制御するための手段をユーザーに提供を担当します。 このコンポーネントは、プロファイリング対象アプリケーションのプロセス領域とは別に独自のプロセス空間で常に実行されます。 Profiler の UI は、アタッチ、トリガー」を呼び出すプロセスでとしても機能できます、 [iclrprofiling::attachprofiler](iclrprofiling-attachprofiler-method.md)分析アプリケーションがそのような場合、プロファイラー DLL しなかった Profiler DLL を読み込むメソッド起動時に読み込みます。

> [!IMPORTANT]
> Profiler UI コントロールおよび Windows ストア アプリでレポートを使用した場合にも Windows デスクトップ アプリケーションでのままする必要があります。 パッケージ化し、Windows ストアで、診断ツールを出荷することを期待しないでください。 ツールは、Windows ストア アプリを実行できないし、Profiler の UI 内にこれらの多くの作業を行う必要があります。

サンプル コードには、このドキュメントでは、全体を前提とします。

- CLR のプロファイル API の要件に従って、ネイティブ DLL をする必要がありますので、C++ では、Profiler DLL が書き込まれます。

- Profiler UI は、c# で記述されます。 必要に応じてはありませんが、Profiler の UI プロセス用の言語の要件がないため、なぜ簡潔で単純である言語を選択しますか。

### <a name="windows-rt-devices"></a>Windows RT デバイス

Windows RT デバイスをロック ダウンは非常にします。 サード パーティ製のプロファイラーだけは読み込めませんなどのデバイスで。 このドキュメントでは、Windows 8 Pc に重点を置いています。

## <a name="consuming-windows-runtime-apis"></a>Windows ランタイム Api を使用

次のセクションで説明したシナリオの数は、Profiler の UI のデスクトップ アプリケーションをいくつかの新しい Windows ランタイム Api を使用する必要があります。 Windows ランタイム Api を使用して、デスクトップ アプリケーションからについてのマニュアルを参照して、アプリ デスクトップ アプリケーションおよび Windows ストアから呼び出すかどうかの動作が異なる場合。

マネージ コードで、Profiler の UI が書き込まれた場合は、いくつかの手順を簡単にこれらの Windows ランタイム Api を使用するために実行する必要がありますがあります。 参照してください、[マネージ デスクトップ アプリと Windows ランタイム](https://go.microsoft.com/fwlink/?LinkID=271858)詳細についてはします。

## <a name="loading-the-profiler-dll"></a>Profiler の DLL の読み込み

このセクションでは、Profiler UI によってどのように、Profiler の DLL を読み込む Windows ストア アプリについて説明します。 このセクションで説明するコードは、Profiler の UI のデスクトップ アプリでが属しており、したがってはデスクトップ アプリについては safe が Windows ストア アプリの必ずしも安全でない Windows Api を使用する必要があります。

Profiler UI には、2 つの方法で、アプリケーションのプロセス領域に読み込まれる Profiler DLL が発生します。

- アプリケーションの起動時、環境変数によって制御されるようにします。

- 呼び出すことによって起動が完了したら、アプリケーションにアタッチすることにより、 [iclrprofiling::attachprofiler](iclrprofiling-attachprofiler-method.md)メソッド。

起動時読み込みと Windows ストア アプリで正しく動作する、Profiler の DLL のアタッチ読み込み、最初の障害の 1 つ受け取ることです。 読み込みの両方の形式は、特別な考慮事項を共通の共有を起動しましょう。

### <a name="common-considerations-for-startup-and-attach-loads"></a>スタートアップの一般的な考慮事項と負荷のアタッチ

**DLL、Profiler の署名**

Windows では、Profiler DLL をロードしようとして、Profiler DLL が正しく署名されていることを確認します。 それ以外の場合は、既定で読み込みに失敗しました。 これには、2 つの方法があります。

- Profiler DLL が署名されていることを確認します。

- インストール必要となる開発者用ライセンス Windows 8 コンピューターに、ツールを使用する前に、ユーザーに伝えます。 これは行えます自動的に Visual Studio から、またはコマンド プロンプトから手動でします。 詳細については、次を参照してください。[開発者用ライセンスを取得](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10))します。

**ファイル システム権限**

Windows ストア アプリはそのファイル システム上の場所から Profiler DLL を実行する権限が必要 residesBy 既定では、Windows ストア アプリは、Profiler の DLL の読み込みに失敗した呼び出そうとするほとんどのディレクトリでこのようなアクセス許可がないです。次のような Windows アプリケーション イベント ログのエントリが生成されます。

```Output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

一般に、Windows ストア アプリは、限られた、ディスク上の場所へのアクセスにのみ使用できます。 各 Windows ストア アプリは、すべての Windows ストア アプリがアクセスを許可、ファイル システムで他のいくつかの領域と同様に、独自のアプリケーション データ フォルダーにアクセスできます。 すべての Windows ストア アプリは、読み取りし、既定では実行のアクセス許可がありますので、Profiler の DLL とその依存関係 Program Files または Program Files (x86) をインストールすることをお勧めします。

### <a name="startup-load"></a>起動時の読み込み

通常、デスクトップ アプリでの Profiler UI メッセージが表示されます、Profiler の DLL の起動負荷必要な CLR のプロファイル API の環境変数が含まれる環境ブロックを初期化することにより (つまり、 `COR_PROFILER`、 `COR_ENABLE_PROFILING`、および`COR_PROFILER_PATH`)、およびその環境ブロックを新しいプロセスを作成します。 Windows ストア アプリの場合も当てはまりますが、メカニズムは異なります。

**管理者特権で実行しないでください。**

プロセス Windows ストア アプリ プロセス B、A のプロセスを起動しようとすると、実行するかどう中度の整合性のレベル、高度な整合性レベル (つまり、引き上げられません) ではなく。 つまり、中度の整合性レベルで、Profiler の UI を実行する必要がありますまたは中程度の整合性レベルの Windows ストア アプリを起動する別のデスクトップ プロセスを起動する必要があります。

**プロファイルを Windows ストア アプリの選択**

最初を起動するには、どの Windows ストア アプリ、profiler のユーザーを確認します。 デスクトップ アプリの場合、ファイルの [参照] ダイアログを表示するなどと、ユーザーが検索して、.exe ファイルを選択します。 Windows ストア アプリは、さまざまな意味をなさない [参照] ダイアログを使用して、します。 代わりに、ユーザーから選択するには、そのユーザー用にインストールされた Windows ストア アプリの一覧を表示することをお勧めします。

使用することができます、<xref:Windows.Management.Deployment.PackageManager>クラスをこの一覧を生成します。 `PackageManager` デスクトップ アプリは、使用可能な Windows ランタイム クラスは、実際には*のみ*デスクトップ アプリを利用できます。

次のコード例でデスクトップ アプリとして記述された仮定 Profiler UI からC#を使用して、 `PackageManager` Windows アプリの一覧を生成します。

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

**カスタムの環境ブロックを指定します。**

新しい COM インターフェイス、 [IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)、いくつかの形式の診断を簡単に Windows ストア アプリの実行動作をカスタマイズすることができます。 そのメソッドでは、いずれかの[EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)を起動すると、環境ブロックを Windows ストア アプリに渡すことができますと自動のプロセスの中断を無効にするように他の便利な効果。 環境変数を指定する必要があるために、環境のブロックが重要です (`COR_PROFILER`、 `COR_ENABLE_PROFILING`、および`COR_PROFILER_PATH)`)、CLR によって、Profiler の DLL を読み込むために使用します。

次のコード スニペットを考えてみます。

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

いくつかの項目を正しく理解する必要があります。

- `packageFullName` パッケージに対する繰り返し処理を更新し、中に決定できます`package.Id.FullName`します。

- `debuggerCommandLine` もう少し興味深いです。 Windows ストア アプリにカスタムの環境ブロックを渡すために、独自の単純なダミー デバッガーを記述する必要があります。 Windows 産み落とす、Windows ストア アプリは中断され、この例のようなコマンドラインを使用して、デバッガーを起動することで、デバッガーをアタッチします。

    ```Output
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     場所`-p 1336`、Windows ストア アプリのプロセス ID の 1336 ことを意味し、`-tid 1424`スレッド ID 1424 が中断されているスレッドであることを意味します。 ダミーのデバッガーは、コマンドラインからスレッド Id を解析、そのスレッドを再開し終了します。

     これを行う C++ コードのいくつかの例を次に示します (エラー チェックを追加することを確認する!)。

    ```cpp
    int wmain(int argc, wchar_t* argv[])
    {
        // …
        // Parse command line here
        // …

        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,
                                                                  FALSE /* bInheritHandle */, nThreadID);
        ResumeThread(hThread);
        CloseHandle(hThread);
        return 0;
    }
    ```

     診断ツールのインストールの一部としてこのダミーのデバッガーを展開しでは、このデバッガーへのパスを指定する必要があります、`debuggerCommandLine`パラメーター。

**Windows ストア アプリを起動します。**

Windows ストア アプリを起動する時点が最後に到着しました。 既に自分で行うをしようとした場合があることに気付きます[CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa)は Windows ストア アプリのプロセスを作成する方法にありません。 代わりに、使用する必要があります、 [IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication)メソッド。 そのためには、起動している Windows ストア アプリのアプリ ユーザー モデル ID を取得する必要があります。 また、マニフェストでドメインを実行する必要がありますを意味します。

パッケージを反復処理中に (「を選択する、Windows ストア アプリをプロファイル」を参照してください、[スタートアップ ロード](#startup-load)前セクション)、現在のパッケージのマニフェストに含まれているアプリケーションのセットを取得します。

```csharp
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";

AppxPackaging.IStream manifestStream;
SHCreateStreamOnFileEx(
                    manifestPath,
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE
                    0,              // file creation attributes
                    false,          // fCreate
                    null,           // reserved
                    out manifestStream);

IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);

IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();
```

はい、1 つのパッケージは、複数のアプリケーションを持つことができ、各アプリケーションには、独自のアプリケーション ユーザー モデル ID したがって、ユーザーのプロファイルには、どのアプリケーションを要求し、その特定のアプリケーションからのアプリケーション ユーザー モデル ID を取得する必要があります。

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

最後に、ようになりましたがある Windows ストア アプリを起動する必要があります。

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

**呼び出す DisableDebugging**

呼び出した場合[IPackageDebugSettings::EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)、呼び出すことによって手動でクリーンアップする約束を作成した、 [IPackageDebugSettings::DisableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging)メソッドであるため、操作を実行しますプロファイリング セッションが上にします。

### <a name="attach-load"></a>負荷をアタッチします。

使用して、Profiler の UI は、その Profiler DLL を既に開始されているを実行しているアプリケーションにアタッチする場合、 [iclrprofiling::attachprofiler](iclrprofiling-attachprofiler-method.md)します。 Windows ストア アプリにも当てはまります。 前述の一般的な考慮事項、だけでなくことを確認しますが、対象の Windows ストア アプリは中断されません。

**EnableDebugging**

呼び出すスタートアップのロードと同様、 [IPackageDebugSettings::EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)メソッド。 環境ブロックに渡す必要はありませんが、その他の機能の 1 つ必要があります。 自動のプロセスの中断を無効にするとします。 それ以外の場合、Profiler UI を呼び出すと[AttachProfiler](iclrprofiling-attachprofiler-method.md)対象の Windows ストア アプリを中断する可能性があります。 実際には、これは、可能性の高い、Profiler の UI を使用した、ユーザーが対話するようになりましたし、Windows ストア アプリがユーザーの画面のいずれかでアクティブでない場合。 かどうか、Windows ストア アプリが中断されたことができなくへの応答には、CLR を送信することに、Profiler の DLL をアタッチすることを通知します。

したがってこのような作業を行う必要があります。

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

これは、同じ呼び出しのために作成するスタートアップ ロードの場合、デバッガーのコマンドラインまたは環境ブロックを指定しない点です。

**DisableDebugging**

いつものように忘れずに呼び出す[IPackageDebugSettings::DisableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging)プロファイリング セッションが完了するとします。

## <a name="running-inside-the-windows-store-app"></a>Windows ストア アプリ内で実行されています。

したがって、Windows ストア アプリには、Profiler DLL が最後に読み込まれます。 Profiler DLL には、Windows ストア アプリで必要な別のルールで再生する方法を学習する必要があります、これは、アクセス許可を削減などを実行する方法と Api は、許容されます。

### <a name="stick-to-the-windows-store-app-apis"></a>Windows ストア アプリの Api を引き続き使用します。

Windows API を参照する場合に、すべての API がデスクトップ アプリ、Windows ストア アプリ、またはその両方に適用されるとして記載されていることがわかります。 たとえば、**要件**のドキュメントのセクションで、 [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)関数は、関数は、デスクトップ アプリのみに適用されることを示します。 これに対し、 [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)関数はデスクトップ アプリと Windows ストア アプリの両方を使用できます。

Profiler DLL を開発するときに、Windows ストア アプリである場合に扱い、他人し、のみ Windows ストア アプリに利用可能として記載されている Api を使用します。 依存関係を分析 (たとえば、実行することができます`link /dump /imports`を監査する、Profiler DLL に対して)、依存関係のうちは、[ok] とはこれを表示するドキュメントを検索します。 Safe として記載されている API の新しいフォームを交換するだけでほとんどの場合、違反を修正することができます (たとえば、置換[InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)で[InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex))。

Profiler DLL は、デスクトップ アプリのみに適用されるいくつかの Api を呼び出すし、まださせる、Windows ストア アプリ内で、Profiler の DLL が読み込まれるときにもいるようなことが分かります。 リスクの高い Windows ストア アプリのプロセスに読み込まれると、Profiler DLL での Windows ストア アプリで使用するために記載されていない任意の API を使用することがあります。

- このような Api は、Windows ストア アプリの実行の一意のコンテキストで呼び出されたときに動作する保証はありません。

- 別の Windows ストア アプリのプロセス内から呼び出されたときに、このような Api が一貫して動作しない可能性があります。

- そのような Api では、Windows の現在のバージョンでの Windows ストア アプリから正常に動作すると思われる場合がありますが、または Windows の将来のリリースで無効にする解除可能性があります。

すべての違反を修正し、リスクを回避することをお勧めします。

絶対に特定の API なしで使用できないを Windows ストア アプリの適切な置換を見つけることができませんがあります。 このような場合は、少なくとも。

- テスト、テスト、その API の使用量から生活 daylights をテストします。

- API の中断または呼び出された場合に表示されなくなる可能性がありますが突然の理解から Windows ストア内のアプリでの将来のリリース Windows。 これは見なされない互換性に関する問題によって、Microsoft と、演算子の使用をサポートしても、優先度はできません。

### <a name="reduced-permissions"></a>権限が制限されました。

デスクトップ アプリと Windows ストア アプリのアクセス許可は異なる方法をすべて一覧に、このトピックの範囲外になります。 確実に動作は、Profiler の DLL (デスクトップ アプリと比較して、Windows ストア アプリに読み込まれる) とすべてのリソースにアクセスしようとするたびに異なるなります。 ファイル システムは、最も一般的な例です。 ありますが、いくつかが特定の Windows ストア アプリのアクセスが許可されているディスク上に配置 (を参照してください[アクセスとアクセス許可をファイル (Windows ランタイム アプリ](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10)))、Profiler DLL は、同じ制限の下になります。 コードを徹底的にテストします。

### <a name="inter-process-communication"></a>プロセス間通信

Profiler DLL (Windows ストア アプリのプロセス領域に読み込まれる) が、独自のカスタム プロセスの間で Profiler UI (デスクトップ アプリを別のプロセス空間内で実行されている) と通信する必要がありますこのホワイト ペーパーの冒頭にある図に示すように通信 (IPC) チャネル。 Profiler の UI では、その動作を変更する Profiler DLL に信号を送信し、Profiler の DLL は、後処理およびプロファイラーのユーザーに表示するための Profiler UI に分析された Windows ストア アプリからデータを送信します。

ほとんどのプロファイラーがこのように動作する必要がありますが、Windows ストア アプリに、Profiler の DLL が読み込まれると、IPC メカニズムの選択内容が制限されています。 たとえば、名前付きパイプ一部ではない SDK、Windows ストア アプリのため、使用することはできません。

ファイルの中より限定的な方法ではあります。 イベントも使用できます。

**ファイルを使用して通信します。**

ほとんどのデータはファイルを使用して、Profiler の DLL と Profiler の UI の可能性があります渡します。 キーは、ファイルの場所 (Windows ストア アプリのコンテキスト) での Profiler の DLL と Profiler の UI の両方を読んだとへの書き込みアクセスを選択します。 たとえば、一時フォルダーのパスは、Profiler の DLL と Profiler の UI の両方からアクセスできる場所が (したがって他の Windows ストア アプリのパッケージからログインするすべての情報をシールドする) 他の Windows ストア アプリ パッケージにアクセスできません。

Profiler の UI と Profiler の DLL パスを特定できるいないこの個別にします。 現在のユーザーにインストールされているすべてのパッケージで反復処理時に、Profiler UI を (前のサンプル コードを参照) へのアクセスを取得する、`PackageId`クラスは、コンピューターをこのスニペットのようなコードの派生元の一時フォルダのパス。 (いつものようにエラー チェックは省略します。)

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

その一方で、Profiler DLL が基本的に同じことで行うことができますより簡単に取得できるか、<xref:Windows.Storage.ApplicationData>クラスを使用して、 [ApplicationData.Current](xref:Windows.Storage.ApplicationData.Current%2A)プロパティ。

**イベントを介して通信します。**

Profiler の UI と Profiler の DLL の間の単純なシグナリング セマンティクスを実行する場合に、Windows ストア アプリとデスクトップ アプリ内でイベントを使用することができます。

Profiler DLL を呼び出すだけでできます、 [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)任意の名前と名前付きイベントを作成する関数。 例:

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

Profiler UI は、Windows ストア アプリの名前空間の下の名前付きイベントを検索する必要があります。 たとえば、Profiler UI を呼び出すことが[CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)、としてイベント名を指定します。

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

`<acSid>` Windows ストア アプリの AppContainer SID です。 このトピックの前のセクションでは、現在のユーザーに対してインストールされているパッケージを反復処理する方法を示しました。 そのサンプル コードからは、パッケージ Id を取得できます。 Id を取得でき、`<acSid>`次のようなコードで。

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a>シャット ダウンの通知はありません。

Windows ストア アプリ内で実行されている、ときに、Profiler の DLL に依存しないでくださいか[icorprofilercallback::shutdown](icorprofilercallback-shutdown-method.md)またはでも[DllMain](/windows/desktop/Dlls/dllmain) (で`DLL_PROCESS_DETACH`) Profiler DLL に通知する呼び出されるWindows ストア アプリが終了しています。 実際が呼び出されないと予想されます。 従来は、多くの Profiler Dll は、ディスク、ファイルを閉じるには、Profiler の UI などに通知を送信するのにキャッシュをフラッシュするのに、便利な場所としてこれらの通知を使用が。ただし、Profiler DLL が少し異なる方法で整理する必要があるようになりました。

Profiler DLL になったので、ログ情報にすることがあります。 パフォーマンス上の理由から、バッチのメモリ内の情報およびバッチの過去のいくつかのしきい値のサイズが増加するようにディスクにフラッシュすることがあります。 まだディスクにフラッシュされていないすべての情報が失われることを前提としています。 つまり、しきい値は、慎重に選択して、Profiler の UI は、Profiler の DLL によって書き込まれた不完全な情報を扱うに書き込まれる必要があります。

## <a name="windows-runtime-metadata-files"></a>Windows ランタイム メタデータ ファイル

詳細に移動するには、このドキュメントの範囲外ですファイルは、どのような Windows ランタイム メタデータ (WinMD) にします。 このセクションでは、WinMD ファイルは、Windows ストア アプリを Profiler DLL の分析によって読み込まれるときに CLR プロファイル API の動作に制限されます。

### <a name="managed-and-non-managed-winmds"></a>マネージ コードと非管理対象の Winmd

開発者は、新しい Windows ランタイム コンポーネント プロジェクトを作成する Visual Studio を使用している場合、そのプロジェクトのビルドは、開発者が作成したメタデータ (クラスやインターフェイスなどの型の説明) を説明する WinMD ファイルを生成します。 このプロジェクトが c# または VB で記述されたマネージ言語のプロジェクトの場合は、これらの型 (つまり、開発者のソース コードからコンパイルされたすべての IL が含まれています) の実装は同じ WinMD ファイルも含まれます。 このようなファイルは、管理対象の WinMD ファイルと呼ばれます。 Windows ランタイム メタデータと基になる実装の両方が含まれている点で興味深いです。

これに対し、開発者は、c++ Windows ランタイム コンポーネント プロジェクトを作成する場合は、そのプロジェクトのビルドには、メタデータのみが格納された WinMD ファイルが生成され、実装は別のネイティブ DLL にコンパイルされます。 同様に、Windows SDK に付属している WinMD ファイルには Windows の一部として出荷される個別のネイティブ Dll にコンパイル実装で、メタデータのみが含まれます。

以下の情報は、両方マネージ Winmd、メタデータと実装が含まれてとに管理されていない Winmd メタデータのみを含めることが適用されます。

### <a name="winmd-files-look-like-clr-modules"></a>WinMD ファイルのように CLR モジュール

CLR に関する限り、すべての WinMD ファイルは、モジュールです。 そのため、CLR のプロファイル API は、WinMD ファイルを読み込むときに、Profiler DLL とその Moduleid とは何か他のマネージ モジュールと同じ方法でように指示します。

Profiler DLL は呼び出すことによって他のモジュールから WinMD ファイルを区別することができます、 [icorprofilerinfo 3::getmoduleinfo2](icorprofilerinfo3-getmoduleinfo2-method.md)メソッドを調べて、`pdwModuleFlags`の出力パラメーター、 [COR_PRF_MODULE_WINDOWS_ランタイム](cor-prf-module-flags-enumeration.md)フラグ。 (これは設定、ModuleID は WinMD を表す場合にのみ)。

### <a name="reading-metadata-from-winmds"></a>Winmd メタデータの読み取り

標準のモジュールなどの WinMD ファイルには使用して読み取ることができるメタデータが含まれて、[メタデータ Api](../../../../docs/framework/unmanaged-api/metadata/index.md)します。 ただし、CLR は、マネージ コードでプログラミングして WinMD ファイルを使用する開発者がより自然なプログラミング エクスペリエンスを実現できますように WinMD のファイルを読み取る際に、.NET Framework の型を Windows ランタイム型をマップします。 これらのマッピングの例については、次を参照してください。 [.NET Framework の Windows ストア アプリのサポートと Windows ランタイム](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)します。

ビューは、プロファイラー取りかかりましょうメタデータ Api を使用する場合: Windows ランタイム、未加工のビュー、またはマップされた .NET Framework ビューか?  回答: が稼働しています。

呼び出すと、 [icorprofilerinfo::getmodulemetadata](icorprofilerinfo-getmodulemetadata-method.md)メソッドなど、メタデータ インターフェイスを取得する WinMD を[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)を設定することもできます[ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)で、`dwOpenFlags`パラメーターがこのマッピングを無効にします。 それ以外の場合、既定では、マッピングを有効になります。 通常、プロファイラーでは、よく理解し、プロファイラーのユーザーに自然に WinMD メタデータ (たとえば、型の名前など) から Profiler DLL を取得する文字列が表示されるように、マッピングを有効にするが保持されます。

### <a name="modifying-metadata-from-winmds"></a>Winmd からメタデータを変更します。

Winmd でメタデータを変更することはサポートされていません。 呼び出す場合、 [icorprofilerinfo::getmodulemetadata](icorprofilerinfo-getmodulemetadata-method.md)メソッド WinMD のファイルし、指定[ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)で、`dwOpenFlags`パラメーターなど、書き込み可能なメタデータ インターフェイスを要求または[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)、 [GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)は失敗します。 これは特に重要に IL の書き換えプロファイラーのインストルメンテーション (たとえば、AssemblyRefs または新しいメソッドを追加する場合など) をサポートするためにメタデータを変更する必要があります。 確認するように[COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md)最初に (前のセクションで説明した) ようし、このようなモジュールで書き込み可能なメタデータ インターフェイスを要求しないようにします。

### <a name="resolving-assembly-references-with-winmds"></a>Winmd でアセンブリの参照を解決します。

多くのプロファイラーは、インストルメンテーションまたは型検査を支援するために手動でメタデータの参照を解決する必要があります。 このようなプロファイラーは、これらの参照は標準のアセンブリ参照を完全に異なる方法で解決されるために、CLR が Winmd、 をポイントするアセンブリ参照を解決する方法を認識する必要があります。

## <a name="memory-profilers"></a>メモリ プロファイラー

ガベージ コレクターとマネージ ヒープは、Windows ストア アプリとデスクトップ アプリで根本的に異なるではありません。 ただし、プロファイラーの作成者が注意する必要があるいくつかの微妙な違いがあります。

### <a name="forcegc-creates-a-managed-thread"></a>ForceGC マネージ スレッドを作成します

Profiler DLL が別のスレッドを呼び出す通常作成メモリのプロファイリングを行うときに、 [ForceGC メソッド](icorprofilerinfo-forcegc-method.md)メソッド。 これは、新しいものはありません。 Windows ストア アプリ内でのガベージ コレクションの処理の動作がマネージ スレッドに、スレッドを変換が驚くべきものがありますが、(たとえば、プロファイル API スレッド Id をそのスレッドの作成されます)。

この結果を理解するのには、CLR プロファイル API で定義されている同期および非同期の呼び出しの間の相違点を理解しておく必要があります。 これは、Windows ストア アプリでの非同期呼び出しの概念から大きく異なることに注意してください。 ブログの投稿を参照してください。 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE あります](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/)詳細についてはします。

関連するポイントは、プロファイラーによって作成されたスレッドで行われた呼び出しは常と見なされること、同期呼び出しが Profiler DLL のいずれかの実装の外部から行われた場合でも[ICorProfilerCallback](icorprofilercallback-interface.md)メソッド。 場合に、少なくともを使用します。 これで、CLR がプロファイラーのスレッドのマネージ スレッドに呼び出しが原因になって[ForceGC メソッド](icorprofilerinfo-forcegc-method.md)スレッドは、プロファイラーのスレッドと見なされなくこと。 そのため、CLR によって適用されると、そのスレッドの同期対象のより厳格な定義-namely からの呼び出しが発生する必要がある Profiler DLL のいずれかの内部[ICorProfilerCallback](icorprofilercallback-interface.md)修飾として同期する方法。

実際にはというは何ですか ほとんど[ICorProfilerInfo](icorprofilerinfo-interface.md)メソッドは安全に同期的に呼び出され、すぐに失敗するそれ以外の場合は。 Profiler DLL を再利用する場合、 [ForceGC メソッド](icorprofilerinfo-forcegc-method.md)通常プロファイラーで作成されたスレッドで行われたその他の呼び出しのスレッド (たとえば、 [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)、 [RequestReJIT](icorprofilerinfo4-requestrejit-method.md)、または[RequestRevert](icorprofilerinfo4-requestrevert-method.md))、問題があるしようとしています。 など、非同期の安全な関数も[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)マネージ スレッドから呼び出されたときに、特別な規則があります。 (ブログの投稿を参照してください。 [Profiler のスタック ウォーク。基本またはそれ以降の](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/)詳細についてはします)。

そのため、ことをお勧め、Profiler の DLL の作成を呼び出す任意のスレッド[ForceGC メソッド](icorprofilerinfo-forcegc-method.md)使用する必要があります*のみ*Gc をトリガーし、GC のコールバックに応答するためにします。 Stack サンプリングまたはデタッチのようなその他のタスクを実行するプロファイリング API を呼び出さないでください。

### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

新しい GC のコールバックでは、以降、.NET Framework 4.5 では、ある[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)、これにより、プロファイラーは、に関する情報を入力するより*依存ハンドル*します。 これらのハンドルは実質的に、GC の有効期間管理するためにターゲット オブジェクトに、ソース オブジェクトからの参照を追加します。 依存ハンドルは目新しいもので、マネージ コードでプログラミングする場合を使用して、独自の依存ハンドルを作成できている、 <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> Windows 8 および .NET Framework 4.5 よりも前にクラス。

ただし、管理対象の XAML Windows ストア アプリは、依存ハンドルの多用をするようになりました。 具体的には、CLR を使用してマネージ オブジェクトと非管理対象の Windows ランタイム オブジェクト間の循環参照の管理を支援するためにします。 つまりよりこれでかつてなく重要とヒープのグラフのエッジの残りを視覚化するようにこれらの依存ハンドルに通知するメモリ プロファイラーであります。 Profiler DLL を使用する必要があります[RootReferences2](icorprofilercallback2-rootreferences2-method.md)、 [ObjectReferences](icorprofilercallback-objectreferences-method.md)、および[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)ヒープ グラフの完全なビューを形成するには.

## <a name="conclusion"></a>まとめ

CLR のプロファイル API を使用して Windows ストア アプリ内で実行されるマネージ コードを分析することになります。 実際には、開発している既存のプロファイラーを実行し、Windows ストア アプリをターゲットにできるように、いくつかの特定の変更を行うことができます。 Profiler UI は、デバッグ モードでの Windows ストア アプリをアクティブ化するための新しい Api を使用する必要があります。 Profiler DLL が Windows ストア アプリの該当する Api のみを使用していることを確認します。 Profiler の DLL と Profiler の UI の間の通信メカニズムが、Windows ストア アプリの API 制限に注意してくださいと Windows ストア アプリ用のアクセス許可の制限の認識に書き込まれます。 Profiler DLL が、CLR は、Winmd を処理する方法を認識する必要がある、ガベージ コレクターの動作がマネージ スレッドに関するさまざまな方法です。

## <a name="resources"></a>リソース

**共通言語ランタイム**

- [プロファイル (アンマネージ API リファレンス)](index.md)

- [メタデータ (アンマネージ API リファレンス)](../metadata/index.md)

**Windows ランタイムと CLR の相互作用**

- [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

**Windows ストア アプリ**

- [ファイル アクセスとアクセス許可 (Windows ランタイム アプリ](https://docs.microsoft.com/previous-versions/windows/apps/hh967755%28v=win.10%29)

- [開発者ライセンスを取得](https://docs.microsoft.com/previous-versions/windows/apps/hh974578%28v=win.10%29)

- [IPackageDebugSettings インターフェイス](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
