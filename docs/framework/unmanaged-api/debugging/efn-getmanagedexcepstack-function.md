---
title: _EFN_GetManagedExcepStack 関数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e201b9a350c030da59e2b6ed27f84f570c8e621
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698383"
---
# <a name="efngetmanagedexcepstack-function"></a>_EFN_GetManagedExcepStack 関数
指定したマネージド例外オブジェクトのアドレスに応じて、中に含まれているスタック トレースの文字列バージョンを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `Client`  
 [in]デバッグ中のクライアント。  
  
 `StackObjAddr`  
 [in]派生したマネージ オブジェクトのポインター<xref:System.Exception>します。  
  
 szStackString  
 [out]返される文字列。  
  
 `cbString`  
 [out]文字列のバッファーで使用できる文字数。  
  
## <a name="remarks"></a>Remarks  
 ないマネージ コードのスレッドで現在のコンテキストの場合、関数は、0xa0 の施設の値と 0x1000 のエラー コードをマネージを返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** SOS_Stacktrace.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
