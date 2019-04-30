---
title: INotifySource2::SetNotifyFilter メソッド
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37e4abeebce155a4c332e864b4dfb6cf5a1141ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940336"
---
# <a name="inotifysource2setnotifyfilter-method"></a>INotifySource2::SetNotifyFilter メソッド
このソースで使用するための通知フィルターが割り当てられます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `in_NotifyFilter`  
 [in]ビットごとの組み合わせ、 [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md)デバッガー API のコールバックを識別する列挙値。  
  
 `in_pUserThreadFilter`  
 [in]ポインターを[USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) API にデバッガー スレッドを識別する構造体。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>関連項目

- [INotifySource2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifyConnection2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [INotifySink2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
