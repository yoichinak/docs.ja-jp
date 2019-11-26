---
title: ISymUnmanagedWriter::DefineGlobalVariable メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: 94d1aa5bba87e8ca11b58bdf89a697e1ccf500b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428025"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a>ISymUnmanagedWriter::DefineGlobalVariable メソッド
Defines a single global variable.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineGlobalVariable(  
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
 `name`  
 [in] A pointer to a `WCHAR` that defines the global variable name.  
  
 `attributes`  
 [in] The global variable attributes.  
  
 `cSig`  
 [in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.  
  
 `signature`  
 [in] The global variable signature.  
  
 `addrKind`  
 [in] The address type.  
  
 `addr1`  
 [in] The first address for the parameter specification.  
  
 `addr2`  
 [in] The second address for the parameter specification.  
  
 `addr3`  
 [in] The third address for the parameter specification.  
  
## <a name="return-value"></a>戻り値  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineLocalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [DefineGlobalVariable2 メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
