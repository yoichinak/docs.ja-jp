---
title: _EFN_GetManagedObjectName 関数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: c7333f8f7b95655ac821e9a2977d5db3794486a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122999"
---
# <a name="_efn_getmanagedobjectname-function"></a>\_EFN\_GetManagedObjectName 関数
指定されたマネージオブジェクトポインターを使用して、型の名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `Client`  
 からデバッグクライアントへのポインター。  
  
 `objAddr`  
 からマネージオブジェクトポインター。  
  
 szName  
 入出力型の名前。  
  
 `cbName`  
 入出力文字列バッファーで使用できる文字数。  
  
## <a name="remarks"></a>Remarks  
 現在コンテキスト内にあるスレッドにマネージコードがない場合、関数は、ファシリティ値が0xa0 で、エラーコードが0x1000 の HRESULT SOS_E_NOMANAGEDCODE を返します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** SOS_Stacktrace  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
