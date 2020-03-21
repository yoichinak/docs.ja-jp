---
title: ICorDebugCode::GetCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178999"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode メソッド
指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。 このメソッドは、.NET Framework バージョン 2.0 では非推奨になりました。 代わりに[、ICorDebugCode2::GetCode チャンクを使用します](icordebugcode2-getcodechunks-method.md)。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `startOffset`  
 [in]関数の先頭のオフセット。  
  
 `endOffset`  
 [in]関数の終了位置のオフセット。  
  
 `cBufferAlloc`  
 [in]コードが`buffer`返される配列のサイズ。  
  
 `buffer`  
 [アウト]コードが返される配列。  
  
 `pcBufferSize`  
 [アウト]返されるバイト数。  
  
## <a name="remarks"></a>解説  
 関数のコードが複数のチャンクに分割されている場合、ネイティブ オフセットを増加させる順に連結されます。 命令の境界はチェックされません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET フレームワークのバージョン:** 1.1、 1.0  
  
## <a name="see-also"></a>関連項目

- [GetCodeChunks メソッド](icordebugcode2-getcodechunks-method.md)
