---
title: _EFN_GetManagedObjectFieldInfo 関数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 675bf2ad36fe5006a44890f8ccd6e6197f264ac1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484473"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a>_EFN_GetManagedObjectFieldInfo 関数
指定したオブジェクト ポインターとフィールド名を使用して、オブジェクトの先頭からフィールドまでのオフセットとフィールドの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `Client`  
 [in]デバッグ クライアントへのポインター。  
  
 `objAddr`  
 [in]マネージ オブジェクトのポインター。  
  
 szFieldName  
 [in]フィールド名にマネージ オブジェクトのポインター。  
  
 `pValue`  
 [out]フィールドの値。 このパラメーターには、null を指定できます。  
  
 `pOffset`  
 [out]オフセット`objAddr`フィールドにします。 このパラメーターには、null を指定できます。  
  
## <a name="remarks"></a>Remarks  
 オフセットが 0 の場合は、オフセットは書き込まれません。  
  
 ないマネージ コードのスレッドで現在のコンテキストの場合、関数は、0xa0 の施設の値と 0x1000 のエラー コードをマネージを返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** SOS_Stacktrace.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
