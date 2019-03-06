---
title: ISymENCUnmanagedMethod::GetLineFromOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90d993bc6b947d309ce1a0fb10ad231a429be567
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471915"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset メソッド
オフセットに関連付けられている行の情報を取得します。 場合オフセット パラメーター (`dwOffset`) がシーケンス ポイントでは、このメソッドは、前のオフセットに関連付けられている行の情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwOffset`  
 [in]A`ULONG32`オフセットを格納しています。  
  
 `pline`  
 [out]ポインターを`ULONG32`行を受け取る。  
  
 `pcolumn`  
 [out]ポインター、`ULONG32`列を受け取る。  
  
 `pendLine`  
 [out]ポインター、`ULONG32`最終行を受け取る。  
  
 `pendColumn`  
 [out]ポインター、`ULONG32`終了列を受け取る。  
  
 `pdwStartOffset`  
 [out]ポインター、`ULONG32`関連付けられているシーケンス ポイントを受け取る。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目
- [ISymENCUnmanagedMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
