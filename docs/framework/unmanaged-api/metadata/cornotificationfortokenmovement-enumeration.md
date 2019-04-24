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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15c5e8b34f2748868611bd7dc47ef73c491b1338
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189431"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement 列挙型
トークンの再マップが発生したときに、メタデータ API クライアントに送信される通知を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
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
|`MDNotifyDefault`|ときの通知`mdTypeRef`、 `mdMethodDef`、 `mdMemberRef`、または`mdFieldDef`トークン移動します。|  
|`MDNotifyAll`|任意のトークンが移動したときに通知します。|  
|`MDNotifyNone`|トークンの移動時に通知しません。|  
|`MDNotifyMethodDef`|ときの通知、`mdMethodDef`トークン移動します。|  
|`MDNotifyMemberRef`|ときの通知、`mdMemberRef`トークン移動します。|  
|`MDNotifyFieldDef`|ときの通知、`mdFieldDef`トークン移動します。|  
|`MDNotifyTypeRef`|ときの通知、`mdTypeRef`トークン移動します。|  
|`MDNotifyTypeDef`|ときの通知、`mdTypeDef`トークン移動します。|  
|`MDNotifyParamDef`|ときの通知、`mdParamDef`トークン移動します。|  
|`MDNotifyInterfaceImpl`|ときの通知、`mdInterfaceImpl`トークン移動します。|  
|`MDNotifyProperty`|ときの通知、`mdProperty`トークン移動します。|  
|`MDNotifyEvent`|ときの通知、`mdEvent`トークン移動します。|  
|`MDNotifySignature`|ときの通知、`mdSignature`トークン移動します。|  
|`MDNotifyTypeSpec`|ときの通知、`mdTypeSpec`トークン移動します。|  
|`MDNotifyCustomAttribute`|ときの通知、`mdCustomAttribute`トークン移動します。|  
|`MDNotifySecurityValue`|ときの通知、`mdSecurityValue`トークン移動します。|  
|`MDNotifyPermission`|ときの通知、`mdPermission`トークン移動します。|  
|`MDNotifyModuleRef`|ときの通知、`mdModuleRef`トークン移動します。|  
|`MDNotifyNameSpace`|ときの通知、`mdNameSpace`トークン移動します。|  
|`MDNotifyAssemblyRef`|ときの通知、`mdAssemblyRef`トークン移動します。|  
|`MDNotifyFile`|ときの通知、`mdFile`トークン移動します。|  
|`MDNotifyExportedType`|ときの通知、`mdExportedType`トークン移動します。|  
|`MDNotifyResource`|ときの通知、`mdManifestResource`トークン移動します。|  
  
## <a name="remarks"></a>Remarks  
 トークンを再マップ (移動) するメタデータのマージ中にします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
