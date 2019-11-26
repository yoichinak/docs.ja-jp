---
title: ISymUnmanagedReader::GetSymAttribute メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
ms.openlocfilehash: 7f04b5c100f1fd9c44e671b883fe469b16d33fa6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440141"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a>ISymUnmanagedReader::GetSymAttribute メソッド
Gets a custom attribute based upon its name. Unlike metadata custom attributes, these custom attributes are held in the symbol store.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `parent`  
 [in] The metadata token for the object for which the attribute is requested.  
  
 `name`  
 [in] A pointer to the variable that indicates the attribute to retrieve.  
  
 `cBuffer`  
 [in] `buffer` 配列のサイズ。  
  
 `pcBuffer`  
 [out] A pointer to the variable that receives the length of the attribute data.  
  
 `buffer`  
 [out] A pointer to the variable that receives the attribute data.  
  
## <a name="return-value"></a>戻り値  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedReader インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
