---
title: ICorProfilerCallback::RemotingClientInvocationStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b452cbfc5564d98b3770c2ed97f8453296f0fc13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992161"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a>ICorProfilerCallback::RemotingClientInvocationStarted メソッド
リモート処理呼び出しが開始されたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a>Remarks  
 このイベントは、同期および非同期の呼び出しに同じです。  
  
 次のコールバックのペアのそれぞれについては、同じスレッドで発生します。  
  
- `RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)  
  
- [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)と[icorprofilercallback::remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
- [Icorprofilercallback::remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)と[icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)  
  
 リモート処理のコールバックの次の問題を認識する必要があります。  
  
- クライアントから呼び出され、サーバー上で実行される関数の通知が正しく受信されていないために、リモート処理関数の実行は、プロファイラー API によって反映されません。 プロキシ オブジェクトによって行われ、実際の呼び出しプロファイラーを特定の関数でが JIT コンパイルしますが、使用されていないと表示されます。  
  
- プロファイラーは、非同期リモート処理イベントの正確な通知を受信しません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
