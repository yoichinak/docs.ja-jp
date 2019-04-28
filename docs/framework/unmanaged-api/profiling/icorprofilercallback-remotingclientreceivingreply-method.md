---
title: ICorProfilerCallback::RemotingClientReceivingReply メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5865935af96260982d47b778d208f4235f6245e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775037"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a>ICorProfilerCallback::RemotingClientReceivingReply メソッド
リモート処理呼び出しのサーバー側の部分が完了し、クライアントが受け取るようになりましたことをプロファイラーに通知し、応答を処理します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a>パラメーター  
 `pCookie`  
 [in]指定された値に対応する値[icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)これらの条件下で。  
  
- リモート処理の GUID の cookie はアクティブです。  
  
- チャネルは、メッセージの送信に成功します。  
  
- GUID の cookie は、サーバー側のプロセスでアクティブにします。  
  
 これにより、リモート処理呼び出しのペアを容易にします。  
  
 `fIsAsync`  
 [in]値が`true`呼び出しが非同期。 それ以外の場合`false`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
