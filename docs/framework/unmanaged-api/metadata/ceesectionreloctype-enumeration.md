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
ms.openlocfilehash: 44a84e0752eecc1c694f3b8cf6e568b72b7d0f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176215"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 列挙型
`reloc` [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)の呼び出しで出力される命令の種類に影響を与える値を提供します。  
  
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
|`srRelocAbsolute`|セクション相対`reloc`部分だけを生成し、.reloc セクションに何も送信しません。|  
|`srRelocHighLow`|ポインター サイズ`reloc`の場所の を生成します。 これは、プラットフォームに応じてBASED_HIGHLOWまたはBASED_DIR64に変換されます。|  
|`srRelocHighAdj`|32`reloc`ビットの数値の上位 16 ビットに対して a を生成し、下の 16 ビットが .reloc テーブルの次の単語に含まれます。|  
|`srRelocMapToken`|トークン マップの再配置を生成し、.reloc セクションに何も送信しません。|  
|`srRelocRelative`|値が相対アドレスフィックスアップであることを示します。|  
|`srRelocFilePos`|セクション相対`reloc`部分だけを生成し、.reloc セクションに何も送信しません。 これは`reloc`セクションの仮想アドレスではなく、セクションのファイル位置を基準にしています。|  
|`srRelocCodeRelative`|コード相対アドレスのフィックスアップを指定します。|  
|`srRelocIA64Imm64`|ia64`reloc``movl`命令で 64 ビットアドレスの a を生成します。|  
|`srRelocDir64`|64`reloc`ビット アドレスの を生成します。|  
|`srRelocIA64PcRel25`|`reloc` ia64`br.call`命令で 25 ビット PC 相対アドレスの を生成します。|  
|`srRelocIA64PcRel64`|ia64`reloc``brl.call`命令で 64 ビット PC 相対アドレスの a を生成します。|  
|`srRelocAbsoluteTagged`|タグ付きポインター値に使用される 30 ビットのセクション相対`reloc`値を生成します。|  
|`srRelocSentinel`|この列挙型への追加が内部`reloc`の名前配列に反映されることを確認するのに役立つセンチネル値。|  
|`srNoBaseReloc`|ベース`reloc`を出力しないことを指定します。|  
|`srRelocPtr`|メモリの修正前の内容がセクション オフセットではなくポインターであることを示す値。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
