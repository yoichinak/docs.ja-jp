---
title: CorValidatorModuleType 列挙型
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: a8dc09ee9f0f0fd79060bb86c599ab40a285153b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448763"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType 列挙型
Specifies the type of a module.  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|The module is an invalid type.|  
|`ValidatorModuleTypeMin`|The minimum value of the `CorValidatorModuleType` enum.|  
|`ValidatorModuleTypePE`|The module is a portable executable (PE) file.|  
|`ValidatorModuleTypeObj`|The module is a .obj file.|  
|`ValidatorModuleTypeEnc`|The module is an edit-and-continue debugger session.|  
|`ValidatorModuleTypeIncr`|The module is one that has been incrementally built.|  
|`ValidatorModuleTypeMax`|The maximum value of the `CorValidatorModuleType` enum.|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
