---
title: CorDebugMappingResult 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2fecc7160cb41e31bf88f1a461265ad8fdce166
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170392"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult 列挙型
命令ポインター (IP) の値が得られた方法の詳細を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Ip アドレスの値は 0 は、プロローグでネイティブ コードです。|  
|`MAPPING_EPILOG`|Ip アドレスの値は、メソッドの最後の命令のアドレスは、エピローグでネイティブ コード。|  
|`MAPPING_NO_INFO`|マッピング情報がない、メソッドの使用可能なため、IP の値は 0 です。|  
|`MAPPING_UNMAPPED_ADDRESS`|メソッドのマッピング情報が、現在のアドレスは、Microsoft intermediate language (MSIL) コードにマップできません。 Ip アドレスの値は 0 です。|  
|`MAPPING_EXACT`|メソッドの MSIL コードに正確にマップまたはフレームが解釈されているので、ip アドレスの値は正確です。|  
|`MAPPING_APPROXIMATE`|メソッドが正常にマップされましたが、ip アドレスの値は概数である可能性があります。|  
  
## <a name="remarks"></a>Remarks  
 使用することができます、 [icordebugilframe::getip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)命令ポインターの値を取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
