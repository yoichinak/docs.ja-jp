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
ms.openlocfilehash: 691041632312bf8ac7c82a11724dcd725e14a420
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231059"
---
# <a name="corfield-structure"></a>COR_FIELD 構造体
オブジェクトのフィールドに関する情報が提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
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
|`token`|`mdFieldDef`フィールド情報を取得するために使用できるトークン。|  
|`offset`|オブジェクトのフィールドのデータへのバイト オフセット。|  
|`id`|A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)をこのフィールドの型を識別する値。|  
|`fieldType`|フィールドの種類を示す CorElementType 列挙値。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
