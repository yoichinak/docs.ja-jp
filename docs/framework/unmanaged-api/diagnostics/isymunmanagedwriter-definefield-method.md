---
title: ISymUnmanagedWriter::DefineField メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fd9798b3681d66e71d5703f4d16564b153da07b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176177"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField メソッド
メソッド内ではない 1 つの変数を定義します。 このメソッドは、使用のクラス内の特定のフィールド、ビット フィールド、および具合です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>パラメーター  
 `parent`  
 [in]メタデータ型またはメソッド トークン。  
  
 `name`  
 [in]フィールド名です。  
  
 `attributes`  
 [in]フィールドの属性。  
  
 `cSig`  
 [in]A`ULONG32`文字のフィールドのシグネチャを格納するために必要なバッファーのサイズはします。  
  
 `signature`  
 [in]フィールドの署名の配列。  
  
 `addrKind`  
 [in]アドレスの種類。  
  
 `addr1`  
 [in]フィールド指定の最初のアドレス。  
  
 `addr2`  
 [in]フィールド指定の 2 番目のアドレス。  
  
 `addr3`  
 [in]フィールド指定の 3 番目のアドレス。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
