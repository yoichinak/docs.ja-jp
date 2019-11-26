---
title: CeeSectionRelocType 列挙型
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
ms.openlocfilehash: efce0c13944b383c42cbff6a6af4795293ee2989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444159"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 列挙型
Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`srRelocAbsolute`|Generates only a section-relative `reloc`, sending nothing into a .reloc section.|  
|`srRelocHighLow`|Generates a `reloc` for a pointer-sized location. This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.|  
|`srRelocHighAdj`|Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.|  
|`srRelocMapToken`|Generates a token map relocation, sending nothing into a .reloc section.|  
|`srRelocRelative`|Indicates that the value is a relative address fixup.|  
|`srRelocFilePos`|Generates only a section-relative `reloc`, sending nothing into a .reloc section. This `reloc` is relative to the file position of the section, not the section's virtual address.|  
|`srRelocCodeRelative`|Specifies a code-relative address fixup.|  
|`srRelocIA64Imm64`|Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.|  
|`srRelocDir64`|Generates a `reloc` for a 64-bit address.|  
|`srRelocIA64PcRel25`|Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.|  
|`srRelocIA64PcRel64`|Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.|  
|`srRelocAbsoluteTagged`|Generates a 30-bit section-relative `reloc`, used for tagged pointer values.|  
|`srRelocSentinel`|A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.|  
|`srNoBaseReloc`|Specifies not to emit a base `reloc`.|  
|`srRelocPtr`|A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
