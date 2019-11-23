---
title: ISymUnmanagedScope::GetNamespaces メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
ms.openlocfilehash: b765294826a5da4010cdd2db79b50667a6f1cdb4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446306"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a>ISymUnmanagedScope::GetNamespaces メソッド
Gets the namespaces that are being used within this scope.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cNameSpaces`  
 [in] `namespaces` 配列のサイズ。  
  
 `pcNameSpaces`  
 [out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.  
  
 `namespaces`  
 [out] The array that receives the namespaces.  
  
## <a name="return-value"></a>戻り値  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedScope インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
