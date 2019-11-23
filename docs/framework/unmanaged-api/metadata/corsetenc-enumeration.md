---
title: CorSetENC 列挙型
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 39f72e670ddc700c257f50f6bad6fab702ec21b6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432774"
---
# <a name="corsetenc-enumeration"></a>CorSetENC 列挙型
メタデータの生成中の動作を決定する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`MDSetENCOn`|互換性のために残されています。|  
|`MDSetENCOff`|互換性のために残されています。|  
|`MDUpdateENC`|Indicates that whereas metadata can be updated, tokens cannot be moved.|  
|`MDUpdateFull`|Indicates that tokens can be moved during updates.|  
|`MDUpdateExtension`|Indicates that updates can consist only of additions. Tokens cannot be moved.|  
|`MDUpdateIncremental`|Indicates that compilation is incremental.|  
|`MDUpdateDelta`|Indicates that only changed metadata should be saved.|  
|`MDUpdateMask`|Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
