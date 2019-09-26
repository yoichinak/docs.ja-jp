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
ms.openlocfilehash: c59ddec655f3127e8dab8d8c41543f03a896cf63
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274032"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT 構造体
マネージド ヒープ上のオブジェクトに関する情報が提供されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
|`size`|オブジェクトの合計サイズ (バイト単位)。|  
|`type`|オブジェクトの型を表す[COR_TYPEID](cor-typeid-structure.md)トークンです。|  
  
## <a name="remarks"></a>コメント  
 `COR_HEAPOBJECT`インスタンスを取得するには、 [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md)メソッドを呼び出すことによって設定される、表示されている[heapheapenum](icordebugheapenum-interface.md)インターフェイスオブジェクトを列挙します。  
  
 インスタンス`COR_HEAPOBJECT`は、マネージヒープ上のライブオブジェクトに関する情報、またはオブジェクトではなく、ガベージコレクターによってまだ収集されていないオブジェクトに関する情報を提供します。  
  
 パフォーマンスを向上させる`COR_HEAPOBJECT.address`ために、 `CORDB_ADDRESS`このフィールドはデバッグ API の多くで使用される ICorDebugValue インターフェイス値ではなく、値になります。 指定されたオブジェクトアドレスの ICorDebugValue オブジェクトを取得するには、 `CORDB_ADDRESS` [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md)メソッドに値を渡すことができます。  
  
 パフォーマンスを向上させる`COR_HEAPOBJECT.type`ために、 `COR_TYPEID`このフィールドは、デバッグ API の多くで使用されている、テキスト型のインターフェイス値ではなく、値です。 指定された型 ID の[ICorDebugProcess5:: gettypefortypeid](icordebugprocess5-gettypefortypeid-method.md)メソッドに`COR_TYPEID`値を渡すことができます。  
  
 構造`COR_HEAPOBJECT`体には、参照カウントの COM インターフェイスが含まれています。 のインスタンスを`COR_HEAPOBJECT`列挙子から取得する場合は、[次のメソッドを](icordebugheapenum-next-method.md)呼び出す必要があります。その後、参照を解放する必要があります。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
