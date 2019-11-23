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
ms.openlocfilehash: 7eea63cae27c08260177dfc7746046b975434611
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428037"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField メソッド
Defines a single variable that is not within a method. This method is used for certain fields in classes, bit fields, and so on.  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in] The metadata type or method token.  
  
 `name`  
 [in] The field name.  
  
 `attributes`  
 [in] The field attributes.  
  
 `cSig`  
 [in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.  
  
 `signature`  
 [in] The array of field signatures.  
  
 `addrKind`  
 [in] The address type.  
  
 `addr1`  
 [in] The first address for the field specification.  
  
 `addr2`  
 [in] The second address for the field specification.  
  
 `addr3`  
 [in] The third address for the field specification.  
  
## <a name="return-value"></a>戻り値  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
