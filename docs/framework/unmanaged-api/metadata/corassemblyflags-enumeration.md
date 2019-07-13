---
title: CorAssemblyFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3532ca0a30d83aa8f61bc4397090f3d589b73257
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780935"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags 列挙型
アセンブリ コンパイルに適用されるメタデータを記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`afPublicKey`|アセンブリ参照が、ハッシュされていない完全な公開キーを保持していることを示します。|  
|`afPA_None`|プロセッサ アーキテクチャが指定されていないことを示します。|  
|`afPA_MSIL`|プロセッサ アーキテクチャがニュートラルであることを示します (PE32)。|  
|`afPA_x86`|プロセッサ アーキテクチャは、x86 (PE32) であることを示します。|  
|`afPA_IA64`|プロセッサ アーキテクチャは、Itanium (pe 32 +) であることを示します。|  
|`afPA_AMD64`|プロセッサ アーキテクチャは、AMD X64 (pe 32 +) であることを示します。|  
|`afPA_ARM`|プロセッサ アーキテクチャは、ARM (PE32) であることを示します。|  
|`afPA_NoPlatform`|アセンブリが参照アセンブリであることを示しますつまり、すべてのアーキテクチャに適用されますが、任意のアーキテクチャ上で実行できません。 したがってと同じでは、フラグ`afPA_Mask`します。|  
|`afPA_Specified`|プロセッサ アーキテクチャのフラグに反映させるかを示す、`AssemblyRef`レコード。|  
|`afPA_Mask`|プロセッサ アーキテクチャを示すマスク。|  
|`afPA_FullMask`|プロセッサ アーキテクチャの説明が含まれることを指定します。|  
|`afPA_Shift`|プロセッサ アーキテクチャのフラグと、インデックスの間でシフト数を示します。|  
|`afEnableJITcompileTracking`|対応する値を示します、<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>の<xref:System.Diagnostics.DebuggableAttribute>します。|  
|`afDisableJITcompileOptimizer`|対応する値を示します、<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>の<xref:System.Diagnostics.DebuggableAttribute>します。|  
|`afRetargetable`|実行時に、別の発行者からのアセンブリにアセンブリを再ターゲットできることを示します。|  
|`afContentType_Mask`|コンテンツの種類を示すマスク。|  
|`afContentType_Default`|既定のコンテンツ タイプを示します。|  
|`afContentType_WindowsRuntime`|Windows ランタイムのコンテンツの種類を示します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
