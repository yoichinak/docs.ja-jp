---
title: INotifySink2::OnSyncCallOut メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: e7b3d5bd53bb9e4d6b897bfbf109c1f7307224cd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442509"
---
# <a name="inotifysink2onsynccallout-method"></a>INotifySink2::OnSyncCallOut メソッド
Gets invoked when a call is out.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `in_CallID`  
 [in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `out_ppBuffer`  
 [out] Call buffer.  
  
 `out_pBufferSize`  
 [out] Size of the call buffer, in bytes.  
  
## <a name="return-value"></a>戻り値  
 S_OK if the method succeeds.  
  
## <a name="requirements"></a>［要件］  
 **Header:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>関連項目

- [INotifySink2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [INotifySource2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifyConnection2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
