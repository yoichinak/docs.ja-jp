---
title: ICorDebugCode2::GetCodeChunks メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84ab475ecb538dcf5bd24c750dfe9c993ea5a0ee
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470901"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks メソッド
このコード オブジェクトを構成しているコード チャンクを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cbufSize`  
 [in]サイズ、`chunks`配列。  
  
 `pcnumChunks`  
 [out]返されるチャンクの数、`chunks`配列。  
  
 `chunks`  
 [out]コードの 1 つのチャンクを表す"CodeChunkInfo"構造体の配列。 場合の値`cbufSize`が 0 の場合このパラメーターを null にすることができます。  
  
## <a name="remarks"></a>Remarks  
 コード チャンクが重複し、は、これが連結されたによって順序に従っている[icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)します。 .NET Framework version 2.0 では、Microsoft intermediate language (MSIL) コード オブジェクトには、1 つのコード チャンクが構成されています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

