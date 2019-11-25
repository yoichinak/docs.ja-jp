---
title: ISymUnmanagedDocument::GetSourceRange メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: 64ecbb56ab32ac8381a4864acd5fd40741786d30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449141"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange メソッド
Returns the specified range of the embedded source into the given buffer. The buffer must be large enough to hold the source.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `startLine`  
 [in] The starting line in the current document.  
  
 `startColumn`  
 [in] The starting column in the current document.  
  
 `endLine`  
 [in] The final line in the current document.  
  
 `endColumn`  
 [in] The final column in the current document.  
  
 `cSourceBytes`  
 [in] The size of the source, in bytes.  
  
 `pcSourceBytes`  
 [out] A pointer to a variable that receives the source size.  
  
 `source`  
 [out] The size and length of the specified range of the source document, in bytes.  
  
## <a name="return-value"></a>戻り値  
 S_OK if the method succeeds.  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedDocument インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
