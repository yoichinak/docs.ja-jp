---
title: CorFieldAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: d28a0c8b7ee85f023026dde6f3cc8f3a8406aa64
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450304"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr 列挙型
フィールドについてのメタデータを記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`fdFieldAccessMask`|Specifies accessibility information.|  
|`fdPrivateScope`|Specifies that the field cannot be referenced.|  
|`fdPrivate`|Specifies that the field is accessible only by its parent type.|  
|`fdFamANDAssem`|Specifies that the field is accessible by derived classes in its assembly.|  
|`fdAssembly`|Specifies that the field is accessible by all types in its assembly.|  
|`fdFamily`|Specifies that the field is accessible only by its type and derived classes.|  
|`fdFamORAssem`|Specifies that the field is accessible by derived classes and by all types in its assembly.|  
|`fdPublic`|Specifies that the field is accessible by all types with visibility of this scope.|  
|`fdStatic`|Specifies that the field is a member of its type rather than an instance member.|  
|`fdInitOnly`|Specifies that the field cannot be changed after it is initialized.|  
|`fdLiteral`|Specifies that the field value is a compile-time constant.|  
|`fdNotSerialized`|Specifies that the field is not serialized when its type is remoted.|  
|`fdSpecialName`|Specifies that the field is special, and that its name describes how.|  
|`fdPinvokeImpl`|Specifies that the field implementation is forwarded through PInvoke.|  
|`fdReservedMask`|Reserved for internal use by the common language runtime.|  
|`fdRTSpecialName`|Specifies that the common language runtime metadata internal APIs should check the encoding of the name.|  
|`fdHasFieldMarshal`|Specifies that the field contains marshaling information.|  
|`fdHasDefault`|Specifies that the field has a default value.|  
|`fdHasFieldRVA`|Specifies that the field has a relative virtual address.|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
