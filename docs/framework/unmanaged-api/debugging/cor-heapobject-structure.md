---
title: COR_HEAPOBJECT 構造体
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f179b58ff8eb51e2843780d3212cf38ed7d13216
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609451"
---
# <a name="corheapobject-structure"></a>COR_HEAPOBJECT 構造体
マネージド ヒープ上のオブジェクトに関する情報が提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`address`|メモリ内のオブジェクトのアドレス。|  
|`size`|(バイト単位)、オブジェクトの合計サイズ。|  
|`type`|A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)オブジェクトの型を表すトークン。|  
  
## <a name="remarks"></a>Remarks  
 `COR_HEAPOBJECT` インスタンスを列挙することによって取得できます、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)インターフェイス オブジェクトの呼び出しによって設定される、 [icordebugprocess 5::enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)メソッド。  
  
 A`COR_HEAPOBJECT`インスタンスか、または任意のオブジェクトでルートがありませんが、ガベージ コレクターによって収集されていないオブジェクトについて、マネージ ヒープ上のライブ オブジェクトに関する情報を提供します。  
  
 パフォーマンスの向上のため、`COR_HEAPOBJECT.address`フィールドは、`CORDB_ADDRESS`値ではなく、ICorDebugValue インターフェイス デバッグ API の多くで使用される値。 指定したオブジェクトのアドレスの ICorDebugValue オブジェクトを取得するには、渡すことができます、`CORDB_ADDRESS`値を[icordebugprocess 5::getobject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)メソッド。  
  
 パフォーマンスの向上のため、`COR_HEAPOBJECT.type`フィールドは、`COR_TYPEID`値ではなく、ICorDebugType インターフェイス デバッグ API の多くで使用される値。 渡す ICorDebugType オブジェクトの指定した型の ID を取得することができます、`COR_TYPEID`値を[icordebugprocess 5::gettypefortypeid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)メソッド。  
  
 `COR_HEAPOBJECT`構造体には、参照カウントの COM インターフェイスが含まれています。 取得する場合、`COR_HEAPOBJECT`を呼び出して列挙子からのインスタンス、 [icordebugheapenum::next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)メソッドでは、後で参照を解放する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
