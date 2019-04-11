---
title: CorRefToDefCheck 列挙型
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82abeb0ce3db075d794787bb1fcd5bc18321bef2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093892"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck 列挙型
コードを最適化するために定義に変換される、参照先アイテムを制御するフラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`MDRefToDefDefault`|定義に変換する必要があります型参照とメンバーの参照を指定します。 これは既定値 (`MDTypeRefToDef` &#124; `MDMemberRefToDef`)。|  
|`MDRefToDefAll`|参照されるすべてのアイテムが定義に変換されることを指定します。|  
|`MDRefToDefNone`|定義に参照されている項目を変換しない必要がありますを指定します。|  
|`MDTypeRefToDef`|型の参照のみが型定義に変換されることを指定します。|  
|`MDMemberRefToDef`|メンバーの参照のみが定義に変換されることを指定します。 つまり、メンバーの参照は、メソッドの定義またはフィールドの定義のいずれかに変換する必要があります。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
