---
title: CorNotificationForTokenMovement 列挙型
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: 411fad0accb59431f776c5bd66e8bd3027ddd907
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450146"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement 列挙型
Specifies the notifications that will be sent to the metadata API client when a token remap occurs.  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`MDNotifyDefault`|Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.|  
|`MDNotifyAll`|Notify when any token moves.|  
|`MDNotifyNone`|Do not notify when tokens move.|  
|`MDNotifyMethodDef`|Notify when an `mdMethodDef` token moves.|  
|`MDNotifyMemberRef`|Notify when an `mdMemberRef` token moves.|  
|`MDNotifyFieldDef`|Notify when an `mdFieldDef` token moves.|  
|`MDNotifyTypeRef`|Notify when an `mdTypeRef` token moves.|  
|`MDNotifyTypeDef`|Notify when an `mdTypeDef` token moves.|  
|`MDNotifyParamDef`|Notify when an `mdParamDef` token moves.|  
|`MDNotifyInterfaceImpl`|Notify when an `mdInterfaceImpl` token moves.|  
|`MDNotifyProperty`|Notify when an `mdProperty` token moves.|  
|`MDNotifyEvent`|Notify when an `mdEvent` token moves.|  
|`MDNotifySignature`|Notify when an `mdSignature` token moves.|  
|`MDNotifyTypeSpec`|Notify when an `mdTypeSpec` token moves.|  
|`MDNotifyCustomAttribute`|Notify when an `mdCustomAttribute` token moves.|  
|`MDNotifySecurityValue`|Notify when an `mdSecurityValue` token moves.|  
|`MDNotifyPermission`|Notify when an `mdPermission` token moves.|  
|`MDNotifyModuleRef`|Notify when an `mdModuleRef` token moves.|  
|`MDNotifyNameSpace`|Notify when an `mdNameSpace` token moves.|  
|`MDNotifyAssemblyRef`|Notify when an `mdAssemblyRef` token moves.|  
|`MDNotifyFile`|Notify when an `mdFile` token moves.|  
|`MDNotifyExportedType`|Notify when an `mdExportedType` token moves.|  
|`MDNotifyResource`|Notify when an `mdManifestResource` token moves.|  
  
## <a name="remarks"></a>Remarks  
 A token may be re-mapped (that is, moved) during a metadata merge.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
