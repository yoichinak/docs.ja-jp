---
title: ISymUnmanagedMethod::GetSequencePoints メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6b1e253fb7bf1a97f44e1eb05676fc356af9837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123709"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints メソッド
このメソッド内のすべてのシーケンス ポイントを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cPoints`  
 [in]A`ULONG32`のサイズを受け取る、 `offsets`、 `documents`、 `lines`、 `columns`、 `endLines`、および`endColumns`配列。  
  
 `pcPoints`  
 [out]ポインター、`ULONG32`シーケンス ポイントの格納に必要なバッファーの長さを受け取る。  
  
 `offsets`  
 [in]シーケンス ポイントに対するメソッドの先頭から language (MSIL) オフセットを Microsoft 中間を格納する配列。  
  
 `documents`  
 [in]シーケンス ポイントが配置されているドキュメントを格納する配列。  
  
 `lines`  
 [in]シーケンス ポイントが配置されているドキュメントの行を格納する配列。  
  
 `columns`  
 [in]シーケンス ポイントが配置されているドキュメント内の列を格納する配列。  
  
 `endLines`  
 [in]シーケンス ポイントが終了するドキュメント内の行の配列。  
  
 `endColumns`  
 [in]シーケンス ポイントが終了するドキュメント内の列の配列。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
