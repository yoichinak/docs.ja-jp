---
title: ICorPublish::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc13ec58e1830e6fb5aab5ae50dfc7a983ffc9f4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499681"
---
# <a name="icorpublishgetprocess-method"></a>ICorPublish::GetProcess メソッド
取得、 [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)指定の識別子を持つプロセスを表すインスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pid`  
 [in]プロセスの識別子です。  
  
 `ppProcess`  
 [out]アドレスへのポインター、`ICorPublishProcess`プロセスを表すインスタンス。  
  
## <a name="remarks"></a>Remarks  
 `GetProcess` プロセスが存在しないか、現在のユーザーがデバッグ可能なマネージ プロセスがない場合は失敗します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorPublish インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
