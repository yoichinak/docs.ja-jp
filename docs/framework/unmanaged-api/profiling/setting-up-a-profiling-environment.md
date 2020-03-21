---
title: プロファイル環境の設定
ms.date: 03/30/2017
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
ms.openlocfilehash: 32ebb868ea64a24fba80133b1a0eb539f51cb411
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176969"
---
# <a name="setting-up-a-profiling-environment"></a>プロファイル環境の設定
> [!NOTE]
> .NET Framework 4 では、プロファイリングに大きな変更が加えられた。  
  
 マネージド プロセス (アプリケーションまたはサービス) は、起動されると、共通言語ランタイム (CLR: Common Language Runtime) を読み込みます。 CLR は、初期化されると、プロファイラーに接続する必要があるかどうかを決定するために、次の 2 つの環境変数を評価します。  
  
- COR_ENABLE_PROFILING: この環境変数が存在し、1 に設定されている場合にのみ、CLR はプロファイラーに接続します。  
  
- COR_PROFILER: COR_ENABLE_PROFILING のチェックに合格した場合、CLR はこの CLSID または ProgID (あらかじめレジストリに格納されている) を持つプロファイラーに接続します。 COR_PROFILER 環境変数は文字列として定義されます。以下に 2 つの例を示します。  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 CLR アプリケーションのプロファイリングを行うには、COR_ENABLE_PROFILING 環境変数および COR_PROFILER 環境変数を設定してから、アプリケーションを実行する必要があります。 また、プロファイラー DLL が登録済みであることも確認してください。  
  
> [!NOTE]
> .NET Framework 4 以降、プロファイラーを登録する必要はありません。  
  
> [!NOTE]
> NET Framework バージョン 2.0、3.0、および 3.5 のプロファイラーを .NET Framework 4 以降のバージョンで使用するには、環境変数COMPLUS_ProfAPI_ProfilerCompatibilitySetting設定する必要があります。  
  
## <a name="environment-variable-scope"></a>環境変数名のスコープ  
 COR_ENABLE_PROFILING 環境変数と COR_PROFILER 環境変数をどのように設定するかによって、これらの変数が影響を及ぼすスコープが決定します。 これらの変数は、次のいずれかの方法で設定できます。  
  
- [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)呼び出しで変数を設定した場合、その変数は、その時点で実行しているアプリケーションにのみ適用されます。 (そのアプリケーションから起動されて環境を継承する他のアプリケーションにも適用されます)。  
  
- コマンド プロンプト ウィンドウで設定した変数は、そのウィンドウから起動したすべてのアプリケーションに適用されます。  
  
- ユーザー レベルで設定した変数は、エクスプローラーを使用して開始するすべてのアプリケーションに適用されます。 変数を設定した後にコマンド プロンプト ウィンドウを開くと、それらの環境設定が表示されます。そのウィンドウから起動するアプリケーションにも同じ設定が適用されます。 ユーザー レベルで環境変数を設定するには、[マイ**コンピュータ**] を右クリックし、[**プロパティ**] をクリック**Environment Variables****します。** **User variables**  
  
- コンピューター レベルで設定した変数は、そのコンピューターで起動するすべてのアプリケーションに適用されます。 そのコンピューターでコマンド プロンプト ウィンドウを開くと、それらの環境設定が表示されます。そのウィンドウから起動するアプリケーションにも同じ設定が適用されます。 つまり、そのコンピューター上のすべてのマネージド プロセスがプロファイラーと共に起動します。 コンピュータ レベルで環境変数を設定するには、[マイ**コンピュータ**] を右クリックし、[**プロパティ**] をクリック**Environment Variables****します。** **System variables** 再起動後、変数はシステム全体で試用できるようになります。  
  
 Windows サービスのプロファイリングを行う場合は、環境変数を設定した後、コンピューターを再起動してプロファイラー DLL を登録する必要があります。 これらの考慮事項の詳細については、「 [Windows サービスのプロファイリング](#windows_service)」を参照してください。  
  
## <a name="additional-considerations"></a>その他の注意点  
  
- プロファイラー クラスは、[インターフェイス](icorprofilercallback-interface.md)を[実装します。](icorprofilercallback2-interface.md) .NET Framework Version 2.0 では、プロファイラーは `ICorProfilerCallback2` を実装する必要があります。 実装していない場合、`ICorProfilerCallback2` は読み込まれません。  
  
- 一度に 1 つのプロファイラーのみが、指定された環境でプロセスのプロファイリングを行うことができます。 2 つの異なるプロファイラーを別々の環境に登録することはできますが、各プロファイラーは別々のプロセスのプロファイリングを行う必要があります。 プロファイラーは、インプロセス COM サーバー DLL として実装する必要があります。この DLL は、プロファイリング対象プロセスと同じアドレス領域にマップされます。 つまり、プロファイラーはインプロセスで実行されます。 .NET Framework では、これ以外の種類の COM サーバーはサポートしていません。 たとえば、プロファイラーがリモート コンピューターからアプリケーションを監視する場合は、各コンピューターにコレクター エージェントを実装する必要があります。 実装したエージェントは、結果をまとめて中央のデータ収集用コンピューターに送信します。  
  
- プロファイラーはインプロセスでインスタンス化される COM オブジェクトであるため、プロファイリングされる各アプリケーションに専用のプロファイラーのコピーが存在します。 したがって、単一のプロファイラー インスタンスが複数のアプリケーションからのデータを処理する必要はありません。 ただし、プロファイラーのログ コードに、他のプロファイリング対象アプリケーションからのログ ファイルの上書きを回避するロジックを追加する必要があります。  
  
## <a name="initializing-the-profiler"></a>プロファイラーの初期化  
 両方の環境変数のチェックに合格すると、CLR は COM `CoCreateInstance` 関数と同様の方法でプロファイルのインスタンスを作成します。 このプロファイルについては、`CoCreateInstance` の直接呼び出しによる読み込みは行われません。 そのため、スレッド処理モデルの設定が必要な `CoInitialize` の呼び出しが回避されます。 次に、CLR はプロ[ファイラーのメソッドを呼](icorprofilercallback-initialize-method.md)び出します。 このメソッドのシグネチャは次のとおりです。  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 プロファイラーは[、ICorProfilerInfo または ICorProfilerInfo2](icorprofilerinfo-interface.md)インターフェイス ポインターを照会[ICorProfilerInfo2](icorprofilerinfo2-interface.md)`pICorProfilerInfoUnk`し、プロファイリング中に後で詳細情報を要求できるように保存する必要があります。  
  
## <a name="setting-event-notifications"></a>イベント通知の設定  
 次に、プロファイラーは[ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md)メソッドを呼び出して、関心のある通知のカテゴリを指定します。 たとえば、関数の Enter および Leave の通知とガベージ コレクションの通知のみを確認する場合は、次のように指定します。  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 通知マスクをこのように設定することによって、プロファイラーで受け取る通知を制限できます。 この方法は、単純なプロファイラーまたは特別な目的を持つプロファイラーを作成するときに役立ちます。 また、プロファイラーが無視するだけの通知を送信するのに消費される CPU 時間が削減されます。  
  
 特定のプロファイラー イベントは変更できません。 つまり、これらのイベントが `ICorProfilerCallback::Initialize` コールバックで設定されるとすぐに、イベントはオフにできなくなり、新しいイベントをオンにすることもできません。 変更できないイベントを変更しようとすると、失敗を表す HRESULT が `ICorProfilerInfo::SetEventMask` から返されます。  
  
<a name="windows_service"></a>
## <a name="profiling-a-windows-service"></a>Windows サービスのプロファイリング  
 Windows サービスのプロファイリングは、共通言語ランタイム アプリケーションのプロファイリングと同様です。 どちらのプロファイリング操作も環境変数で有効にできます。 Windows サービスはオペレーティング システムの起動時に開始されるため、前の環境変数をあらかじめ作成し、必要な値を設定しておく必要があります。 さらに、プロファイル DLL を事前にシステムに登録しておく必要もあります。  
  
 環境変数 COR_ENABLE_PROFILING と COR_PROFILER を設定し、プロファイラー DLL を登録したら、これらの変更が Windows サービスで検出されるようにするために、ターゲット コンピューターを再起動してください。  
  
 これらの変更を行うと、プロファイリングがシステム全体で有効になります。 以降に実行するすべてのマネージド アプリケーションがプロファイルされるのを避けるには、ターゲット コンピューターを再起動した後で、システム環境変数を削除します。  
  
 この方法では、すべての CLR プロセスもプロファイリングの対象になります。 プロファイラーは、現在のプロセスが対象かどうかを検出するコールバックを初期化するロジックを[ICorProfilerCallback::初期化](icorprofilercallback-initialize-method.md)する必要があります。 プロファイリングの対象ではない場合、プロファイラーは、初期化を実行せずにコールバックからエラーを返すことができます。  
  
## <a name="see-also"></a>関連項目

- [プロファイリングの概要](profiling-overview.md)
