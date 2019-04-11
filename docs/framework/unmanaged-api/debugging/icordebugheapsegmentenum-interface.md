---
title: ICorDebugHeapSegmentEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73036d1c12c46cbfda8031073a005bc9b376040e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137645"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum インターフェイス
マネージド ヒープのメモリ領域の列挙子を提供します。 このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Next メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|指定した数を取得[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープの領域に関する情報が含まれているインスタンス。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugHeapSegmentEnum` ICorDebugEnum インターフェイスを実装するインターフェイス。  
  
 `ICorDebugHeapSegmentEnum`インスタンスには、 [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)インスタンスを呼び出すことによって、 [icordebugprocess 5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)メソッド。 [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)呼び出すことによって、コレクション内のオブジェクトを列挙することができます、 [icordebugheapsegmentenum::next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)メソッド。  
  
 `ICorDebugHeapSegmentEnum`コレクション オブジェクトがマネージ オブジェクトを含む可能性のあるすべてのメモリ領域を列挙しますが、管理対象のオブジェクトが実際にそれらのリージョン内にあることは保証されません。 これには、空または予約済みのメモリ領域に関する情報が含まれます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
