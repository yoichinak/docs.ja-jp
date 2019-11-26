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
ms.openlocfilehash: 86720cb1739e3f193cd1d5081577d69bca1cf0f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427052"
---
# <a name="setting-up-a-profiling-environment"></a>プロファイル環境の設定
> [!NOTE]
> There have been substantial changes to profiling in the .NET Framework 4.  
  
 マネージド プロセス (アプリケーションまたはサービス) は、起動されると、共通言語ランタイム (CLR: Common Language Runtime) を読み込みます。 CLR は、初期化されると、プロファイラーに接続する必要があるかどうかを決定するために、次の 2 つの環境変数を評価します。  
  
- COR_ENABLE_PROFILING: この環境変数が存在し、1 に設定されている場合にのみ、CLR はプロファイラーに接続します。  
  
- COR_PROFILER: COR_ENABLE_PROFILING のチェックに合格した場合、CLR はこの CLSID または ProgID (あらかじめレジストリに格納されている) を持つプロファイラーに接続します。 COR_PROFILER 環境変数は文字列として定義されます。以下に 2 つの例を示します。  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 CLR アプリケーションのプロファイリングを行うには、COR_ENABLE_PROFILING 環境変数および COR_PROFILER 環境変数を設定してから、アプリケーションを実行する必要があります。 また、プロファイラー DLL が登録済みであることも確認してください。  
  
> [!NOTE]
> Starting with the .NET Framework 4, profilers do not have to be registered.  
  
> [!NOTE]
> To use .NET Framework versions 2.0, 3.0, and 3.5 profilers in the .NET Framework 4 and later versions, you must set the COMPLUS_ProfAPI_ProfilerCompatibilitySetting environment variable.  
  
## <a name="environment-variable-scope"></a>環境変数名のスコープ  
 COR_ENABLE_PROFILING 環境変数と COR_PROFILER 環境変数をどのように設定するかによって、これらの変数が影響を及ぼすスコープが決定します。 これらの変数は、次のいずれかの方法で設定できます。  
  
- If you set the variables in an [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) call, they will apply only to the application that you are running at the time. (そのアプリケーションから起動されて環境を継承する他のアプリケーションにも適用されます)。  
  
- コマンド プロンプト ウィンドウで設定した変数は、そのウィンドウから起動したすべてのアプリケーションに適用されます。  
  
- ユーザー レベルで設定した変数は、エクスプローラーを使用して開始するすべてのアプリケーションに適用されます。 変数を設定した後にコマンド プロンプト ウィンドウを開くと、それらの環境設定が表示されます。そのウィンドウから起動するアプリケーションにも同じ設定が適用されます。 To set environment variables at the user level, right-click **My Computer**, click **Properties**, click the **Advanced** tab, click **Environment Variables**, and add the variables to the **User variables** list.  
  
- コンピューター レベルで設定した変数は、そのコンピューターで起動するすべてのアプリケーションに適用されます。 そのコンピューターでコマンド プロンプト ウィンドウを開くと、それらの環境設定が表示されます。そのウィンドウから起動するアプリケーションにも同じ設定が適用されます。 つまり、そのコンピューター上のすべてのマネージド プロセスがプロファイラーと共に起動します。 To set environment variables at the computer level, right-click **My Computer**, click **Properties**, click the **Advanced** tab, click **Environment Variables**, add the variables to the **System variables** list, and then restart your computer. 再起動後、変数はシステム全体で試用できるようになります。  
  
 Windows サービスのプロファイリングを行う場合は、環境変数を設定した後、コンピューターを再起動してプロファイラー DLL を登録する必要があります。 For more information about these considerations, see the section [Profiling a Windows Service](#windows_service).  
  
## <a name="additional-considerations"></a>その他の考慮事項  
  
- The profiler class implements the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfaces. .NET Framework Version 2.0 では、プロファイラーは `ICorProfilerCallback2` を実装する必要があります。 実装していない場合、`ICorProfilerCallback2` は読み込まれません。  
  
- 一度に 1 つのプロファイラーのみが、指定された環境でプロセスのプロファイリングを行うことができます。 2 つの異なるプロファイラーを別々の環境に登録することはできますが、各プロファイラーは別々のプロセスのプロファイリングを行う必要があります。 プロファイラーは、インプロセス COM サーバー DLL として実装する必要があります。この DLL は、プロファイリング対象プロセスと同じアドレス領域にマップされます。 つまり、プロファイラーはインプロセスで実行されます。 .NET Framework では、これ以外の種類の COM サーバーはサポートしていません。 たとえば、プロファイラーがリモート コンピューターからアプリケーションを監視する場合は、各コンピューターにコレクター エージェントを実装する必要があります。 実装したエージェントは、結果をまとめて中央のデータ収集用コンピューターに送信します。  
  
- プロファイラーはインプロセスでインスタンス化される COM オブジェクトであるため、プロファイリングされる各アプリケーションに専用のプロファイラーのコピーが存在します。 したがって、単一のプロファイラー インスタンスが複数のアプリケーションからのデータを処理する必要はありません。 ただし、プロファイラーのログ コードに、他のプロファイリング対象アプリケーションからのログ ファイルの上書きを回避するロジックを追加する必要があります。  
  
## <a name="initializing-the-profiler"></a>プロファイラーの初期化  
 両方の環境変数のチェックに合格すると、CLR は COM `CoCreateInstance` 関数と同様の方法でプロファイルのインスタンスを作成します。 このプロファイルについては、`CoCreateInstance` の直接呼び出しによる読み込みは行われません。 そのため、スレッド処理モデルの設定が必要な `CoInitialize` の呼び出しが回避されます。 The CLR then calls the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) method in the profiler. このメソッドのシグネチャは次のとおりです。  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 The profiler must query `pICorProfilerInfoUnk` for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interface pointer and save it so that it can request more information later during profiling.  
  
## <a name="setting-event-notifications"></a>イベント通知の設定  
 The profiler then calls the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to specify which categories of notifications it is interested in. たとえば、関数の Enter および Leave の通知とガベージ コレクションの通知のみを確認する場合は、次のように指定します。  
  
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
  
 この方法では、すべての CLR プロセスもプロファイリングの対象になります。 The profiler should add logic to its [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback to detect whether the current process is of interest. プロファイリングの対象ではない場合、プロファイラーは、初期化を実行せずにコールバックからエラーを返すことができます。  
  
## <a name="see-also"></a>関連項目

- [プロファイルの概要](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
