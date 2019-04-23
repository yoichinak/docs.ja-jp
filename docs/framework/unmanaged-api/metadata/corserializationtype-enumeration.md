---
title: CorSerializationType 列挙型
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15b1f6be2dac6bc7566852791ac22e495949521c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179630"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType 列挙型
共通言語ランタイムによってオブジェクトをシリアル化する方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|オブジェクトのシリアル化が定義されていません。|  
|`SERIALIZATION_TYPE_BOOLEAN`|オブジェクトがブール型としてシリアル化します。|  
|`SERIALIZATION_TYPE_CHAR`|オブジェクトは、文字型としてシリアル化します。|  
|`SERIALIZATION_TYPE_I1`|オブジェクトは、1 バイトの符号付き整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_U1`|オブジェクトは 1 バイトの符号なし整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_I2`|オブジェクトは、2 バイトの符号付き整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_U2`|オブジェクトが 2 バイトの符号なし整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_I4`|オブジェクトは、4 バイトの符号付き整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_U4`|オブジェクトは、4 バイトの符号なし整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_I8`|オブジェクトは、8 バイトの符号付き整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_U8`|オブジェクトは 8 バイトの符号なし整数としてシリアル化します。|  
|`SERIALIZATION_TYPE_R4`|オブジェクトは、4 バイト浮動小数点としてシリアル化されます。|  
|`SERIALIZATION_TYPE_R8`|オブジェクトは、8 バイトの浮動小数点としてシリアル化されます。|  
|`SERIALIZATION_TYPE_STRING`|オブジェクトは、System.String 型としてシリアル化します。|  
|`SERIALIZATION_TYPE_SZARRAY`|オブジェクトは、1 次元、としてシリアル化 0 下限値の配列。|  
|`SERIALIZATION_TYPE_TYPE`|オブジェクトがジェネリック型としてシリアル化します。|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|オブジェクトは、タグが付けられたオブジェクトとしてシリアル化します。|  
|`SERIALIZATION_TYPE_FIELD`|オブジェクトは、フィールドとしてシリアル化されます。|  
|`SERIALIZATION_TYPE_PROPERTY`|オブジェクトがプロパティとしてシリアル化します。|  
|`SERIALIZATION_TYPE_ENUM`|オブジェクトは、列挙体としてシリアル化されます。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
