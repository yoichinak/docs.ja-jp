---
title: CorGCReferenceType 列挙型
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: eafae181c74d9f3842f7f0d547bcccbbb28c09e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132119"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType 列挙型
ガベージ コレクトされる必要のあるオブジェクトのソースを識別します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー名|説明|  
|-----------------|-----------------|  
|`CorHandleStrong`|オブジェクト ハンドル テーブルからの強い参照へのハンドル。|  
|`CorHandleStrongPinning`|オブジェクトハンドルテーブルからの固定された強い参照へのハンドル。|  
|`CorHandleWeakShort`|オブジェクトハンドルテーブルからの弱い参照へのハンドル。|  
|`CorHandleWeakRefCount`|オブジェクトハンドルテーブルからの弱い参照カウントオブジェクトへのハンドル。|  
|`CorHandleStrongRefCount`|オブジェクトハンドルテーブルからの参照カウントオブジェクトへのハンドル。|  
|`CorHandleStrongDependent`|オブジェクトハンドルテーブルからの依存オブジェクトへのハンドル。|  
|`CorHandleStrongAsyncPinned`|オブジェクト ハンドル テーブルからの非同期固定オブジェクト。|  
|`CorHandleStrongSizedByref`|ガベージ コレクション時に、すべてのオブジェクトおよびオブジェクト ルートの集合的なクロージャの概算サイズを保持する強力なハンドル。|  
|`CorReferenceStack`|マネージスタックからの参照。|  
|`CorReferenceFinalizer`|ファイナライザーキューからの参照。|  
|CorHandleStrongOnly|ハンドルテーブルからの強い参照だけを返します。 この値は、 [ICorDebugProcess5:: EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドによってのみ使用されます。|  
|`CorHandleWeakOnly`|ハンドルテーブルからの弱い参照だけを返します。 この値は、 [ICorDebugProcess5:: EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドによってのみ使用されます。|  
|`CorHandleAll`|Handle テーブルからすべての参照を返します。 この値は、 [ICorDebugProcess5:: EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドによってのみ使用されます。|  
  
## <a name="remarks"></a>Remarks  
 `CorGCReferenceType` 列挙体は次のように使用されます。  
  
- [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)構造体の `type` フィールドの値として、参照またはハンドルのソースを示します。  
  
- [ICorDebugProcess5:: EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドの `types` 引数として、列挙体に含めるハンドルの種類を指定します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
