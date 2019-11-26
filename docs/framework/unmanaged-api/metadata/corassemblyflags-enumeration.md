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
ms.openlocfilehash: fda890cee5f513ea8cf7e82e710f5451a860c49f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443912"
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
|`afPublicKey`|Indicates that the assembly reference holds the full, unhashed public key.|  
|`afPA_None`|Indicates that the processor architecture is unspecified.|  
|`afPA_MSIL`|Indicates that the processor architecture is neutral (PE32).|  
|`afPA_x86`|Indicates that the processor architecture is x86 (PE32).|  
|`afPA_IA64`|Indicates that the processor architecture is Itanium (PE32+).|  
|`afPA_AMD64`|Indicates that the processor architecture is AMD X64 (PE32+).|  
|`afPA_ARM`|Indicates that the processor architecture is ARM (PE32).|  
|`afPA_NoPlatform`|Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture. Thus, the flag is the same as `afPA_Mask`.|  
|`afPA_Specified`|Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.|  
|`afPA_Mask`|A mask that describes the processor architecture.|  
|`afPA_FullMask`|Specifies that the processor architecture description is included.|  
|`afPA_Shift`|Indicates a shift count in the processor architecture flags to and from the index.|  
|`afEnableJITcompileTracking`|Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afDisableJITcompileOptimizer`|Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afRetargetable`|Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.|  
|`afContentType_Mask`|A mask that describes the content type.|  
|`afContentType_Default`|Indicates the default content type.|  
|`afContentType_WindowsRuntime`|Indicates the Windows Runtime content type.|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
