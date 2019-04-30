---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 442584cffe4b4ae44702892587e261d41abf4e8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940245"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a>ISymENCUnmanagedMethod::GetSourceExtentInDocument メソッド
取得では、特定のドキュメントでメソッドの最大の終了行と行を最小を開始します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a>パラメーター  
 `document`  
 [in]ドキュメントへのポインター。  
  
 `pstartLine`  
 [out]ポインターを`ULONG32`開始行を受け取る。  
  
 `pendLine`  
 [out]ポインター、`ULONG32`最終行を受け取る。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymENCUnmanagedMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
