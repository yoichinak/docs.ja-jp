---
title: COR_FIELD 構造体
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f857f773f02da25fe6650000be777b8290f5af91
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274056"
---
# <a name="cor_field-structure"></a>COR_FIELD 構造体
オブジェクトのフィールドに関する情報が提供されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`token`|フィールド情報を取得するために使用できるトークン。`mdFieldDef`|  
|`offset`|オブジェクト内のフィールドデータへのオフセット (バイト単位)。|  
|`id`|このフィールドの型を識別する[COR_TYPEID](cor-typeid-structure.md)値。|  
|`fieldType`|フィールドの型を示す CorElementType 列挙値。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
