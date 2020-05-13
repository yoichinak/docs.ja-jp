---
title: ICorDebugHeapSegmentEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: c9999961ec20a31cf82d5ad60104bcdd04c340d1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210177"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next メソッド
マネージヒープのメモリ領域に関する情報を格納している、指定した数の[COR_HEAPOBJECT](cor-heapobject-structure.md)インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 celt  
 から取得するセグメントの数。  
  
 セグメント  
 入出力ポインターの配列。各ポインターは、マネージヒープ内のメモリ領域に関する情報を提供する[COR_HEAPOBJECT](cor-heapobject-structure.md)オブジェクトを指します。  
  
 pceltFetched  
 入出力実際にで返される[COR_HEAPOBJECT](cor-heapobject-structure.md)オブジェクトの数へのポインター `segments` 。 `celt` が 1 の場合、この値は`null` になることがあります。  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugHeapSegmentEnum インターフェイス](icordebugheapsegmentenum-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
