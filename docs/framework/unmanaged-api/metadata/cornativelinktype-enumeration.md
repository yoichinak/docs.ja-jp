---
title: CorNativeLinkType 列挙型
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66d650adb39a9c7dade0936ec671ae5a8b4aeecd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170073"
---
# <a name="cornativelinktype-enumeration"></a>CorNativeLinkType 列挙型
ネイティブ コード内のリンクの種類を示す値を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`nltNone`|キーワードのいずれも指定されていることを示します。|  
|`nltAnsi`|ANSI キーワードが指定されていることを示します。|  
|`nltUnicode`|Unicode キーワードが指定されていることを示します。|  
|`nltAuto`|Auto キーワードが指定されていることを示します。|  
|`nltOle`|OLE キーワードが指定されていることを示します。|  
|`nltMaxValue`|使用しません。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
