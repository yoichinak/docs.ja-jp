---
title: CorPinvokeMap 列挙型
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 17b7af7016cf88fd3ae263dd952502d515b0c833
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441561"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap 列挙型
Specifies options for a PInvoke call.  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pmNoMangle`|Use each member name as specified.|  
|`pmCharSetMask`|予約済み。|  
|`pmCharSetNotSpec`|予約済み。|  
|`pmCharSetAnsi`|Marshal strings as multiple-byte character strings.|  
|`pmCharSetUnicode`|Marshal strings as Unicode 2-byte characters.|  
|`pmCharSetAuto`|Automatically marshal strings appropriately for the target operating system. The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.|  
|`pmBestFitUseAssem`|予約済み。|  
|`pmBestFitEnabled`|Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.|  
|`pmBestFitDisabled`|Do not perform best-fit mapping of Unicode characters. In this case, all unmappable characters will be replaced by a ‘?’.|  
|`pmBestFitMask`|予約済み。|  
|`pmThrowOnUnmappableCharUseAssem`|予約済み。|  
|`pmThrowOnUnmappableCharEnabled`|Throw an exception when the interop marshaler encounters an unmappable character.|  
|`pmThrowOnUnmappableCharDisabled`|Do not throw an exception when the interop marshaler encounters an unmappable character.|  
|`pmThrowOnUnmappableCharMask`|予約されています。|  
|`pmSupportsLastError`|Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.|  
|`pmCallConvMask`|予約されています。|  
|`pmCallConvWinapi`|Use the default platform calling convention. For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.|  
|`pmCallConvCdecl`|Use the `Cdecl` calling convention. In this case, the caller cleans the stack. This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).|  
|`pmCallConvStdcall`|Use the `StdCall` calling convention. In this case, the callee cleans the stack. This is the default convention for calling unmanaged functions with platform invoke.|  
|`pmCallConvThiscall`|Use the `ThisCall` calling convention. In this case, the first parameter is the `this` pointer and is stored in register ECX. Other parameters are pushed on the stack. The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.|  
|`pmCallConvFastcall`|予約済み。|  
|`pmMaxValue`|予約済み。|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
