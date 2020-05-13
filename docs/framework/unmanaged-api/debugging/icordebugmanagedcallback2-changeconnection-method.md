---
title: ICorDebugManagedCallback2::ChangeConnection メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: 2c6ed14f9238d653b15d26dec9d954c05238817c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213453"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection メソッド
指定した接続に関連付けられたタスクのセットが変更されたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pProcess`  
 から変更された接続を格納しているプロセスを表す "いいプロセス" オブジェクトへのポインター。  
  
 `dwConnectionId`  
 から変更された接続の ID。  
  
## <a name="remarks"></a>Remarks  
 `ChangeConnection`コールバックは、次のいずれかの場合に発生します。  
  
- デバッガーが接続を含むプロセスにアタッチする場合。 この場合、ランタイムは、プロセス内の各接続に対して[ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md)イベントとイベントを生成してディスパッチし `ChangeConnection` ます。 `ChangeConnection`接続のタスクセットが作成後に変更されたかどうかに関係なく、既存のすべての接続に対してイベントが生成されます。  
  
- ホストが[ホスティング API](../hosting/index.md)で[ICLRDebugManager:: setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)を呼び出すとき。  
  
 デバッガーは、新しい変更を取得するために、プロセス内のすべてのスレッドをスキャンする必要があります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback2 インターフェイス](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
