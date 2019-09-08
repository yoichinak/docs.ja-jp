---
title: IDENTITY_ATTRIBUTE 構造体
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0bcabb32d50b236d42a555c073b50ba3a234dde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796489"
---
# <a name="identity_attribute-structure"></a>IDENTITY_ATTRIBUTE 構造体
[IDefinitionIdentity](idefinitionidentity-interface.md)インスタンスに関するメタデータ属性情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pszNamespace`|属性が含まれている名前空間を含む null で終わる文字列へのポインター。|  
|`pszName`|属性の名前を含む null で終わる文字列へのポインター。|  
|`pszValue`|属性の値を格納している null で終わる文字列へのポインター。|  
  
## <a name="remarks"></a>Remarks  
 構造`IDENTITY_ATTRIBUTE`体には、null で終わる文字列への3つのポインターが含まれています。 これら3つの文字列は、1つの属性を表します。  
  
 `IDENTITY_ATTRIBUTE`構造体のインスタンスは、 [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md)構造体のインスタンスに関連付けられています。 構造体には実際の文字列が含まれ`IDENTITY_ATTRIBUTE_BLOB` 、対応する構造体には、 `IDENTITY_ATTRIBUTE`構造体に示されている3つの文字列へのオフセットが一覧表示されます。 `IDENTITY_ATTRIBUTE`  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IDefinitionIdentity インターフェイス](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB 構造体](identity-attribute-blob-structure.md)
- [Fusion 構造体](fusion-structures.md)
