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
ms.openlocfilehash: cb970d31fb5158adc7dbcbb7cc0175cc91c83c8c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107342"
---
# <a name="identityattribute-structure"></a>IDENTITY_ATTRIBUTE 構造体
メタデータ属性について説明する[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pszNamespace`|属性はで、名前空間を含む null で終わる文字列へのポインター。|  
|`pszName`|属性の名前を含む null で終わる文字列へのポインター。|  
|`pszValue`|属性の値を含む null で終わる文字列へのポインター。|  
  
## <a name="remarks"></a>Remarks  
 `IDENTITY_ATTRIBUTE`構造体が null で終わる文字列への 3 つのポインターが含まれています。 これら 3 つの文字列には、1 つの属性について説明します。  
  
 インスタンス、`IDENTITY_ATTRIBUTE`構造のインスタンスに関連付け、 [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)構造体。 `IDENTITY_ATTRIBUTE`実際の文字列と、対応する構造に含まれる`IDENTITY_ATTRIBUTE_BLOB`構造で表示されている 3 つの文字列にオフセットを一覧表示、`IDENTITY_ATTRIBUTE`構造体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IDefinitionIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB 構造体](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [Fusion 構造体](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
