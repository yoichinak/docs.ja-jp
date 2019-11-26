---
title: INotifyConnection2::UnregisterNotifySource メソッド
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: cf399d0c7dec7528f02988ddfe6ca5c0b1f0c4c3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440985"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a>INotifyConnection2::UnregisterNotifySource メソッド
Removes a specified notification source object from the connection.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `in_pNotifySource`  
 [in] Notification object to be unregistered.  
  
## <a name="return-value"></a>戻り値  
 S_OK if the method succeeds.  
  
## <a name="requirements"></a>［要件］  
 **Header:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>関連項目

- [INotifyConnection2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [INotifySource2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifySink2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [RegisterNotifySource メソッド](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
