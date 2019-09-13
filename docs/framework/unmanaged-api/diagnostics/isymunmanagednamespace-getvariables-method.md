---
title: ISymUnmanagedNamespace::GetVariables メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 813f57377c1885b09190ada3c73f4391a3f2d931
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895051"
---
# <a name="isymunmanagednamespacegetvariables-method"></a>ISymUnmanagedNamespace::GetVariables メソッド
この名前空間内のグローバルスコープで定義されているすべての変数を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cVars`  
 から配列の`pVars`サイズを示す。 `ULONG32`  
  
 `pcVars`  
 入出力名前空間を格納`ULONG32`するために必要なバッファーのサイズを受け取るへのポインター。  
  
 `pVars`  
 入出力名前空間を格納しているバッファーへのポインター。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK を返します。それ以外の場合は E_FAIL またはその他のエラーコードを返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedNamespace インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
