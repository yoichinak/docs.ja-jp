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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adef1010d08561c0a0fe38480fe0d2f519a80b49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133524"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind 列挙体
メモリ アドレスの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```  
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
|`ADDR_IL_OFFSET`|Microsoft intermediate language (MSIL) ローカル変数またはパラメーター インデックスを示します。|  
|`ADDR_NATIVE_RVA`|モジュールへの相対仮想アドレスを示します。|  
|`ADDR_NATIVE_REGISTER`|CPU レジスタを示します。|  
|`ADDR_NATIVE_REGREL`|最初のアドレスは、レジスタと 2 番目のアドレスは、オフセットを示します。|  
|`ADDR_NATIVE_OFFSET`|ベース アドレスからのオフセットを示します。|  
|`ADDR_NATIVE_REGREG`|最初のアドレスは、レジスタの下位部、2 つ目は高い部分を示します。|  
|`ADDR_NATIVE_REGSTK`|最初のアドレスは、レジスタの下位部、2 つ目は、高の部分では、および 3 番目のオフセットは、ことを示します。|  
|`ADDR_NATIVE_STKREG`|最初のアドレスは、レジスタこと、2 つ目は、オフセット、および 3 番目はレジスタの高い部分を示します。|  
|`ADDR_BITFIELD`|最初のアドレスは、フィールドの最初と 2 番目のアドレスは、フィールド長のことを示します。|  
|`ADDR_NATIVE_ISECTOFFSET`|最初のアドレスは、セクションと 2 番目のアドレスは、オフセットを示します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断列挙体](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
