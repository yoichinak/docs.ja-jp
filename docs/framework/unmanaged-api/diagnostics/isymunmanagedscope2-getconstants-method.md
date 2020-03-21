---
title: ISymUnmanagedScope2::GetConstants メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176618"
---
# <a name="isymunmanagedscope2getconstants-method"></a>ISymUnmanagedScope2::GetConstants メソッド
このスコープ内で定義されているローカル定数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cConstants`  
 [in]パラメーターが指すバッファーの`pcConstants`長さ。  
  
 `pcConstants`  
 [アウト]定数を`ULONG32`格納するために必要なバッファーのサイズ (文字数) を受け取るを指すポインター。  
  
 `constants`  
 [アウト]定数を格納するバッファー。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合はS_OK。それ以外の場合は、E_FAILまたはその他のエラー コードを返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** コーシム.idl,コーシム.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedScope2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
