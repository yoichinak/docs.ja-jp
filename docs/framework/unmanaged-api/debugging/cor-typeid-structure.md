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
ms.openlocfilehash: 51104516008ffee0694c72733cb5f82b5ba6d8cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609458"
---
# <a name="cortypeid-structure"></a>COR_TYPEID 構造体
型識別子が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`token1`|最初のトークンです。|  
|`token2`|2 つ目のトークンです。|  
  
## <a name="remarks"></a>Remarks  
 `COR_TYPEID`数ガベージ コレクトされるオブジェクトに関する情報を提供するデバッグの方法で構造体が返されます。 その項目に関する追加情報を提供するその他のデバッグ方法の引数として渡すことができます。 たとえば、列挙することによって、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)オブジェクト、個々 が取得することができます[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープ上の個々 のオブジェクトを表すオブジェクト。 渡すことができますし、`COR_TYPEID`値から、`COR_HEAPOBJECT.type`フィールドを[icordebugprocess 5::gettypefortypeid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)オブジェクトに関する型情報を提供する ICorDebugType オブジェクトを取得します。  
  
 A`COR_TYPEID`オブジェクトが不透明にする対象としています。 個別のフィールドをアクセスまたは操作する必要があります。 として指定された識別子として唯一使用することは、`out`メソッドの呼び出しと、ことができるパラメーターは、追加情報を提供するその他のメソッドに渡される、します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
