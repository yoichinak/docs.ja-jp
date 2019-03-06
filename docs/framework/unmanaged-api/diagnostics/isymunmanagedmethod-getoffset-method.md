---
title: ISymUnmanagedMethod::GetOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4537d3098223ebfade6b0351aca4f889d6b2ae2a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471668"
---
# <a name="isymunmanagedmethodgetoffset-method"></a>ISymUnmanagedMethod::GetOffset メソッド
ドキュメント内の位置を指定するには、対応するこのメソッド内のオフセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  
 `document`  
 [in]オフセットを要求する対象のドキュメントへのポインター。  
  
 `line`  
 [in]オフセットを要求する対象のドキュメント行。  
  
 `column`  
 [in]オフセットが要求されるドキュメント列。  
  
 `pRetVal`  
 [out]ポインター、`ULONG32`オフセットを受け取る。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目
- [ISymUnmanagedMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
