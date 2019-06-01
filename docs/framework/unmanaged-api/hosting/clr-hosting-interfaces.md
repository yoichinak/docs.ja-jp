---
title: CLR ホスト インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80404e65263aa4ad245a8c8213630a4736bd7b11
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456875"
---
# <a name="clr-hosting-interfaces"></a>CLR ホスト インターフェイス
アンマネージ インターフェイスについて説明をアプリケーションに共通言語ランタイム (CLR) を統合するホストを使用できます。 情報は、.NET Framework version 2.0 およびそれ以降のバージョンに関係します。 これらのインターフェイスは、ホストのランタイム バージョン 1.0 および 1.1 では、いたよりもさらに多くの制御を有効にして、CLR とホストの実行モデルのより緊密に統合を提供します。  
  
 .NET framework version 1.0 および 1.1 では、ホスティング モデルでは、アンマネージ ホストに、CLR を読み込むプロセス、イベント通知を受信して、特定の設定を構成するを有効になります。 ただし、一般に、ホストと CLR 個別に実行されてそのプロセスにします。 .NET Framework version 2.0 以降のバージョンでは、新しい抽象化レイヤーは、現在、Win32 アセンブリ内の型によって提供されるリソースの多くを提供し、一連のホストが構成可能な機能を拡張するホストを使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [IActionOnCLREvent インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 登録済みのイベントのコールバックを実行するメソッドを提供します。  
  
 [IApartmentCallback インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 アパートメント内でのコールバックを行うためのメソッドを提供します。  
  
 [IAppDomainBinding インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 実行時構成の設定のメソッドを提供します。  
  
 [ICatalogServices インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 カタログ サービスのメソッドを提供します。 (このインターフェイスは、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 [ICLRAssemblyIdentityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 ホストと、CLR アセンブリの間の通信をサポートするメソッドを提供します。  
  
 [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 ホストではなく、CLR によって読み込まれるアセンブリの一覧を管理します。  
  
 [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 ホストにアクセスし、CLR のさまざまな側面を構成するためのメソッドを提供します。  
  
 [ICLRDebugManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 ホスト id とフレンドリ名を関連付ける一連のタスクを有効にする方法を提供します。  
  
 [ICLRErrorReportingManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 エラー報告用にカスタムのヒープ ダンプを構成するホストを有効にする方法を提供します。  
  
 [ICLRGCManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 ホストが CLR のガベージ コレクション システムとの対話を可能にするメソッドを提供します。  
  
 [ICLRHostBindingPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 ホストを評価し、アセンブリのポリシー情報の変更を通知するためのメソッドを提供します。  
  
 [ICLRHostProtectionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 特定のマネージ クラス、メソッド、プロパティ、およびフィールドを部分的に信頼されたコードでの実行をブロックするホストを有効にします。  
  
 [ICLRIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 ホストが、指定された I/O 要求の状態の CLR に通知できるようにするコールバック メソッドを実装します。  
  
 [ICLRMemoryNotificationCallback インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 ホストが、Win32 のと同様の手法を使用してメモリ不足の状態を報告できるように`CreateMemoryResourceNotification`関数。  
  
 [ICLROnEventManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 ホストが登録および CLR イベントのコールバックを登録解除を有効にする方法を提供します。  
  
 [ICLRPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 ポリシー エラーやタイムアウトが発生した場合に実行されるアクションを指定するホストを有効にする方法を提供します。  
  
 [ICLRProbingAssemblyEnum インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 ホストを作成し、その id を理解したりしなくても、clr の内部にあるアセンブリの id 情報を使用してアセンブリのプローブの id を取得できるようにするメソッドを提供します。  
  
 [ICLRReferenceAssemblyEnum インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 ホスト ファイルまたはアセンブリの id データを作成し、それらの id を理解したりしなくても、clr の内部にあるを使用してストリームによって参照されるアセンブリのセットを操作できるようにするメソッドを提供します。  
  
 [ICLRRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 同様の機能を提供します。 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)、ホスト コントロールのインターフェイスを設定する追加のメソッドを使用します。  
  
 [ICLRSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 要求されたタスクに関する情報を取得し、その同期実装でデッドロックを検出するために、ホストのメソッドを提供します。  
  
 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 ホストまたは関連するタスクについて、CLR に通知を提供する、clr の要求を行うことができるようにするメソッドを提供します。  
  
 [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 ホストが CLR に新しいタスクを作成し、現在実行中のタスクを取得し、地理的な言語とタスクのカルチャを設定することを明示的に要求できるようにするメソッドを提供します。  
  
 [ICLRValidator インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告するためのメソッドを提供します。  
  
 [ICorConfiguration インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 CLR を構成するためのメソッドを提供します。  
  
 [ICorThreadpool インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 スレッド プールにアクセスするためのメソッドを提供します。  
  
 [IDebuggerInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 デバッグ サービスの状態に関する情報を取得するためのメソッドを提供します。  
  
 [IDebuggerThreadControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 デバッグ サービスによるスレッドのブロックおよびブロックについて、ホストを通知するメソッドを提供します。  
  
 [IGCHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 ガベージ コレクション システムに関する情報を取得するため、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。  
  
 [IGCHost2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 提供、 [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)ホストがガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズの値より大きいに設定できるようにメソッド`DWORD`します。  
  
 [IGCHostControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 ガベージ コレクターは、仮想メモリの制限を変更するホストを要求できるようにするメソッドを提供します。  
  
 [IGCThreadControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 本来はガベージ コレクションがブロックされるスレッドのスケジューリングに参加するためのメソッドを提供します。  
  
 [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 ホストまたはホストが CLR によって読み込む必要のあるアセンブリのセットを指定するを有効にする方法を提供します。  
  
 [IHostAssemblyStore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 アセンブリと CLR とは無関係にモジュールを読み込むホストを有効にする方法を提供します。  
  
 [IHostAutoEvent インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 ホストによって実装される自動リセット イベントの表現を提供します。  
  
 [IHostControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 アセンブリの読み込みを設定して、ホストがサポートするホスト インターフェイスを決定するためのメソッドを提供します。  
  
 [IHostCrst インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 ホストのスレッドのクリティカル セクションの表現として機能します。  
  
 [IHostGCManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 ガベージ コレクションのメカニズムが CLR によって実装内のイベントのホストに通知するメソッドを提供します。  
  
 [IHostIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 ホストによって提供される I/O 完了ポートと対話する CLR を有効にする方法を提供します。  
  
 [IHostMalloc インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 CLR ホストを通じてヒープから詳細な割り当てを要求するためのメソッドを提供します。  
  
 [IHostManualEvent インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 手動リセット イベントの表現のホストの実装を提供します。  
  
 [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Win32 仮想メモリの標準の関数を使用する代わりに、ホストで仮想メモリの要求を行う CLR のメソッドを提供します。  
  
 [IHostPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 ホストの場合、CLR を実行するアクションの中止、タイムアウト、またはエラーを通知するメソッドを提供します。  
  
 [IHostSecurityContext インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 ホストによって実装されるセキュリティ コンテキスト情報を維持するために CLR を有効にします。  
  
 [IHostSecurityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 アクセスを有効にして、現在実行中のスレッドのセキュリティ コンテキストを制御するメソッドを提供します。  
  
 [IHostSemaphore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 ホストによって実装されるセマフォの表現を提供します。  
  
 [IHostSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 CLR が同期の Win32 関数を使用する代わりに、ホストを呼び出すことによって同期プリミティブを作成するためのメソッドを提供します。  
  
 [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 タスクを管理するホストと通信するために CLR を有効にする方法を提供します。  
  
 [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 標準のオペレーティング システムのスレッドやファイバーの関数を使用する代わりに、ホストを通じてタスクを使用する CLR を有効にする方法を提供します。  
  
 [IHostThreadPoolManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 CLR スレッド プールを構成して、作業項目をスレッド プール キューのメソッドを提供します。  
  
 [IManagedObject インターフェイス](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 マネージ オブジェクトを制御するためのメソッドを提供します。  
  
 "IObjectHandle"  
 ラップ解除の値渡しのマーシャ リングするオブジェクトの間接参照メソッドを提供します。  
  
 [ITypeName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 型名の情報を取得するためのメソッドを提供します。 (このインターフェイスは、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 [ITypeNameBuilder インターフェイス](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 型名を構築するためのメソッドを提供します。 (このインターフェイスは、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 [ITypeNameFactory インターフェイス](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 型名を分解するためのメソッドを提供します。 (このインターフェイスは、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 "IValidator"  
 ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告するためのメソッドを提供します。  
  
## <a name="related-sections"></a>関連項目  
 [非推奨の CLR のホスト インターフェイスおよびコクラス](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 .NET Framework version 1.0 および 1.1 で提供されるホスティング インターフェイスについて説明するトピックが含まれています。  
  
 [.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 .NET Framework 4 で提供されるホスティング インターフェイスについて説明するトピックが含まれています。
