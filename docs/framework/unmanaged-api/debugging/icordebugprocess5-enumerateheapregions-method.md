---
title: ICorDebugProcess5::EnumerateHeapRegions メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61e30cf4ffe45578f7ad37de8295d227dbf313c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61930196"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions メソッド
マネージ ヒープのメモリの範囲の列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppRegions`  
 [out]アドレスへのポインター、 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)オブジェクトがマネージ ヒープ内に存在するメモリの範囲の列挙子は、インターフェイス オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 呼び出しの前に、`ICorDebugProcess5::EnumerateHeapRegions`メソッドを呼び出す必要があります、 [icordebugprocess 5::getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)メソッドの値を確認し、 `areGCStructuresValid` 、返されたフィールド[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)現在の状態でガベージ コレクション ヒープが列挙可能なことを確認するオブジェクト。 さらに、`ICorDebugProcess5::EnumerateHeapRegions`メソッドを返します。 `E_FAIL` 、プロセスの有効期間が早すぎるでアタッチする場合は、作成する前にメモリ領域は。  
  
 このメソッドは、管理対象のオブジェクトを含む可能性のあるすべてのメモリ領域を列挙することが保証がマネージ オブジェクトが実際にそれらのリージョン内にあることは保証されません。 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)コレクション オブジェクトが空または予約済みのメモリ領域を含めることができます。  
  
 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)インターフェイス オブジェクトを列挙できる ICorDebugEnum インターフェイスから派生した標準の列挙子は、 [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)オブジェクト。 各[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)オブジェクトは、そのセグメント内のオブジェクトの生成と、特定のセグメントのメモリの範囲に関する情報を提供します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
