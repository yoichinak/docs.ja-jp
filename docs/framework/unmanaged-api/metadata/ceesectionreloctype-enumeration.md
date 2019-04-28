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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882242da493c49a2e6aa09888e9503dcf2933589
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906140"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 列挙型
種類に影響する値を提供`reloc`への呼び出しで出力される命令[iceegen::addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
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
|`srRelocAbsolute`|生成のみセクション-相対的な`reloc`.reloc セクションに何も送信します。|  
|`srRelocHighLow`|生成、`reloc`のポインター-サイズの場所。 これは、プラットフォームによって BASED_HIGHLOW または BASED_DIR64 に変換されます。|  
|`srRelocHighAdj`|生成、`reloc`上部、下部にある 16 ビットが .reloc テーブルでは、次の単語に含まれる、32 ビットの番号の 16 ビットの。|  
|`srRelocMapToken`|.Reloc セクションに何も返さないトークン マップ再配置を生成します。|  
|`srRelocRelative`|値が相対アドレスのフィックス アップであることを示します。|  
|`srRelocFilePos`|生成のみセクション-相対的な`reloc`.reloc セクションに何も送信します。 これは、`reloc`セクションの仮想アドレスではなく、セクションのファイルの位置に対する相対パスです。|  
|`srRelocCodeRelative`|フィックス アップをコードの相対アドレスを指定します。|  
|`srRelocIA64Imm64`|生成、 `reloc` ia64 に 64 ビット アドレス`movl`命令。|  
|`srRelocDir64`|生成、 `reloc` 64 ビットのアドレス。|  
|`srRelocIA64PcRel25`|生成、 `reloc` ia64 で 25 ビット PC の相対アドレスの`br.call`命令。|  
|`srRelocIA64PcRel64`|生成、 `reloc` ia64 に 64 ビット PC の相対アドレスの`brl.call`命令。|  
|`srRelocAbsoluteTagged`|30 ビット セクションの相対パスが生成されます`reloc`のタグが付けられたポインター値に使用されます。|  
|`srRelocSentinel`|この列挙型への追加機能を確保しやすく、sentinel 値は、内部に反映`reloc`名の配列。|  
|`srNoBaseReloc`|基本を出力しないように指定`reloc`します。|  
|`srRelocPtr`|メモリの事前修正内容のセクションではなく、ポインターを示す値のオフセット。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
