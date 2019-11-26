---
title: CorAttributeTargets 列挙型
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 5f83cb96e39b257a1d35786130cd5ed31d071de7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443871"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets 列挙型
属性を適用できるアプリケーション要素を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =   
        catAssembly | catModule | catClass | catStruct |   
        catEnum | catConstructor | catMethod | catProperty |   
        catField | catEvent | catInterface | catParameter |   
        catDelegate | catGenericParameter,  
  
    catClassMembers        =   
        catClass | catStruct | catEnum | catConstructor |   
        catMethod | catProperty | catField | catEvent |   
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`catAssembly`|Attribute can be applied to an assembly.|  
|`catModule`|Attribute can be applied to a portable executable (.dll or .exe) module.|  
|`catClass`|Attribute can be applied to a class.|  
|`catStruct`|Attribute can be applied to a structure; that is, a value type.|  
|`catEnum`|Attribute can be applied to an enumeration.|  
|`catConstructor`|Attribute can be applied to a constructor.|  
|`catMethod`|Attribute can be applied to a method.|  
|`catProperty`|Attribute can be applied to a property.|  
|`catField`|Attribute can be applied to a field.|  
|`catEvent`|Attribute can be applied to an event.|  
|`catInterface`|Attribute can be applied to an interface.|  
|`catParameter`|Attribute can be applied to a parameter.|  
|`catDelegate`|Attribute can be applied to a delegate.|  
|`catGenericParameter`|Attribute can be applied to a generic parameter.|  
|`catAll`|Attribute can be applied to any application element.|  
|`catClassMembers`|Attribute can be applied to a member of a class.|  
  
## <a name="remarks"></a>Remarks  
 The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.  
  
 The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
