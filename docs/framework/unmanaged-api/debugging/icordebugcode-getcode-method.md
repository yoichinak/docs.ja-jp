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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e18097dd380ee354e5652886544d40da074f1230
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747622"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode メソッド
指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。 このメソッドは、.NET Framework version 2.0 で廃止されました。 使用[icordebugcode 2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)代わりにします。  
  
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
 [in]関数の最初のオフセット。  
  
 `endOffset`  
 [in]関数の最後のオフセット。  
  
 `cBufferAlloc`  
 [in]サイズ、`buffer`にコードを返される配列。  
  
 `buffer`  
 [out]コードが返される先の配列。  
  
 `pcBufferSize`  
 [out]返されるバイト数。  
  
## <a name="remarks"></a>Remarks  
 関数のコードは、複数のチャンクに分割されていますが場合、は、ネイティブのオフセットの昇順で連結されます。 命令の境界はチェックされません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1, 1.0  
  
## <a name="see-also"></a>関連項目

- [GetCodeChunks メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
