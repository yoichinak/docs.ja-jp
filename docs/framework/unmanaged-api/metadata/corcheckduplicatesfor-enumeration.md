---
title: CorCheckDuplicatesFor 列挙型
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d04f5589ecffbcde59a6ffbe4f3d6c5f0b1040cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074873"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor 列挙型
重複のチェックとメタデータ トークンを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =   
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |   
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`MDDupAll`|すべてのメタデータ トークンの重複を確認します。|  
|`MDDupENC`|使用しません。|  
|`MDNoDupChecks`|メタデータ トークンの重複をチェックしません。|  
|`MDDupTypeDef`|重複をチェック`mdTypeDef`トークンです。|  
|`MDDupInterfaceImpl`|重複をチェック`mdInterfaceImpl`トークンです。|  
|`MDDupMethodDef`|重複をチェック`mdMethodDef`トークンです。|  
|`MDDupTypeRef`|重複をチェック`mdTypeRef`トークンです。|  
|`MDDupMemberRef`|重複をチェック`mdMemberRef`トークンです。|  
|`MDDupCustomAttribute`|重複をチェック`mdCustomAttribute`トークンです。|  
|`MDDupParamDef`|重複をチェック`mdParamDef`トークンです。|  
|`MDDupPermission`|重複をチェック`mdPermission`トークンです。|  
|`MDDupProperty`|重複をチェック`mdProperty`トークンです。|  
|`MDDupEvent`|重複をチェック`mdEvent`トークンです。|  
|`MDDupFieldDef`|重複をチェック`mdFieldDef`トークンです。|  
|`MDDupSignature`|重複をチェック`mdSignature`トークンです。|  
|`MDDupModuleRef`|重複をチェック`mdModuleRef`トークンです。|  
|`MDDupTypeSpec`|重複をチェック`mdTypeSpec`トークンです。|  
|`MDDupImplMap`|重複をチェック`mdImplMap`トークンです。|  
|`MDDupAssemblyRef`|重複をチェック`mdAssemblyRef`トークンです。|  
|`MDDupFile`|重複をチェック`mdFile`トークンです。|  
|`MDDupExportedType`|重複をチェック`mdExportedType`トークンです。|  
|`MDDupManifestResource`|重複をチェック`mdManifestResource`トークンです。|  
|`MDDupGenericParam`|重複をチェック`mdGenericParam`トークンです。|  
|`MDDupMethodSpec`|重複をチェック`mdMethodSpec`トークンです。|  
|`MDDupGenericParamConstraint`|重複をチェック`mdGenericParamConstraint`トークンです。|  
|`MDDupAssembly`|重複をチェック`mdAssembly`トークンです。|  
|`MDDupDefault`|重複をチェック`mdMemberRef`、 `mdTypeRef`、 `mdSignature`、 `mdTypeSpec`、および`mdMethodSpec`トークンです。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
