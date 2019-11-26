---
title: ISymUnmanagedENCUpdate::UpdateMethodLines メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
ms.openlocfilehash: 9aace77c4b3549c033433d4c305b07daa1f7a8c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448996"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a>ISymUnmanagedENCUpdate::UpdateMethodLines メソッド
Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently. A delta for each statement is allowed.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mdMethodToken`  
 [in] The metadata of the method token.  
  
 `pDeltas`  
 [in] An array of `INT32` values that indicates deltas for each sequence point in the method.  
  
 `cDeltas`  
 [in] A `ULONG` containing the size of the `pDeltas` parameter.  
  
## <a name="return-value"></a>戻り値  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedENCUpdate インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
