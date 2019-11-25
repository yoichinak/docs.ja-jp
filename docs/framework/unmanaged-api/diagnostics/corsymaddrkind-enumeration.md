---
title: CorSymAddrKind 列挙体
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: 12f31d0bf224e38418818122dad3586ec687b2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448577"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind 列挙体
Indicates the type of memory address.  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.|  
|`ADDR_NATIVE_RVA`|Indicates a relative virtual address into a module.|  
|`ADDR_NATIVE_REGISTER`|Indicates a CPU register.|  
|`ADDR_NATIVE_REGREL`|Indicates that the first address is a register and the second address is an offset.|  
|`ADDR_NATIVE_OFFSET`|Indicates an offset from a base address.|  
|`ADDR_NATIVE_REGREG`|Indicates that the first address is the low portion of a register, and the second address is the high portion.|  
|`ADDR_NATIVE_REGSTK`|Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.|  
|`ADDR_NATIVE_STKREG`|Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.|  
|`ADDR_BITFIELD`|Indicates that the first address is the start of a field and the second address is the field length.|  
|`ADDR_NATIVE_ISECTOFFSET`|Indicates that the first address is the section and the second address is an offset.|  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断列挙型](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
