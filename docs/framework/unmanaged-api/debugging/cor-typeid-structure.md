---
title: COR_TYPEID 構造体
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273996"
---
# <a name="cor_typeid-structure"></a>COR_TYPEID 構造体
型識別子が含まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`token1`|最初のトークン。|  
|`token2`|2番目のトークン。|  
  
## <a name="remarks"></a>コメント  
 構造`COR_TYPEID`体は、ガベージコレクションされるオブジェクトに関する情報を提供する多数のデバッグメソッドによって返されます。 その後、その項目に関する追加情報を提供する他のデバッグメソッドに引数として渡すことができます。 たとえば、COR_HEAPOBJECT [ICorDebugHeapEnum](icordebugheapenum-interface.md)オブジェクトを列挙することによって、マネージヒープ上の個々のオブジェクトを表す個々の[COR_HEAPOBJECT](cor-heapobject-structure.md)オブジェクトを取得できます。 次に、 `COR_HEAPOBJECT.type`フィールドの`COR_TYPEID`値を[ICorDebugProcess5:: gettypefortypeid](icordebugprocess5-gettypefortypeid-method.md)メソッドに渡して、オブジェクトに関する型情報を提供する、テキストオブジェクトを取得します。  
  
 `COR_TYPEID`オブジェクトは不透明であることが想定されています。 個々のフィールドにアクセスしたり操作したりすることはできません。 唯一の用途は、メソッドの呼び出しで`out`パラメーターとして指定された識別子として使用され、さらに情報を提供するために他のメソッドに渡すことができます。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
