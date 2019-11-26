---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
ms.openlocfilehash: 2063856389b122b150a2d2744169a4a567592287
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446452"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a>ISymUnmanagedReader2::GetMethodByVersionPreRemap メソッド
Gets a symbol reader method, given a method token and an edit-and-continue version number. Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  
 `token`  
 [in] The method metadata token.  
  
 `version`  
 [in] The method version.  
  
 `pRetVal`  
 [out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.  
  
## <a name="return-value"></a>戻り値  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl. CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedReader2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
