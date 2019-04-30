---
title: ISymUnmanagedWriter::DefineSequencePoints メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 735b33ac1f049f8d4d3740239e7c34a6fa16dd32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969170"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints メソッド
現在のメソッド内のシーケンス ポイントのグループを定義します。 各開始行と開始列は、メソッド内のステートメントの先頭を定義します。 それぞれの終了行と列の終了は、メソッド内のステートメントの末尾を定義します。 配列は、オフセットの昇順に並べ替える必要があります。 オフセットは常に (バイト単位)、メソッドの先頭から測定されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `document`  
 [in]シーケンス ポイントが定義されているドキュメント オブジェクト。  
  
 `spCount`  
 [in]A`ULONG32`のそれぞれのサイズを示す、 `offsets`、 `lines`、 `columns`、 `endLines`、および`endColumns`バッファー。  
  
 `offsets`  
 [in]シーケンス ポイントのオフセットは、メソッドの先頭から計測されます。  
  
 `lines`  
 [in]シーケンス ポイントの開始行番号。  
  
 `columns`  
 [in]シーケンス ポイントの開始列番号。  
  
 `endLines`  
 [in]シーケンス ポイントの終了行番号。 このパラメーターは省略できます。  
  
 `endColumns`  
 [in]シーケンス ポイントの終了列番号。 このパラメーターは省略できます。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
