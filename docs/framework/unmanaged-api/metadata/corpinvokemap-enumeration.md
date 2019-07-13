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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a876ff1ba0d2342f7975bf5adfc8ec03d21578f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781641"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap 列挙型
PInvoke 呼び出しのオプションを指定します。  
  
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
|`pmNoMangle`|指定された各メンバー名を使用します。|  
|`pmCharSetMask`|予約済み。|  
|`pmCharSetNotSpec`|予約済み。|  
|`pmCharSetAnsi`|マルチ バイト文字の文字列として文字列をマーシャ リングします。|  
|`pmCharSetUnicode`|Unicode 2 バイト文字の文字列をマーシャ リングします。|  
|`pmCharSetAuto`|自動的に対象のオペレーティング システムを適切に文字列をマーシャ リングします。 既定値は Unicode では、Windows NT、Windows 2000、Windows XP、および Windows Server 2003 ファミリです。既定値はし、Windows 98 および Windows me では ANSI|  
|`pmBestFitUseAssem`|予約済み。|  
|`pmBestFitEnabled`|ANSI 文字セットで一致がない Unicode 文字の最適なマッピングを実行します。|  
|`pmBestFitDisabled`|Unicode 文字の最適なマッピングを実行しません。 この場合、すべてのマップできない文字に置き換えられます、'?' です。|  
|`pmBestFitMask`|予約済み。|  
|`pmThrowOnUnmappableCharUseAssem`|予約済み。|  
|`pmThrowOnUnmappableCharEnabled`|相互運用マーシャラーは、マップできない文字を検出した場合は、例外をスローします。|  
|`pmThrowOnUnmappableCharDisabled`|相互運用マーシャラーは、マップできない文字を検出したときに例外をスローしません。|  
|`pmThrowOnUnmappableCharMask`|予約されています。|  
|`pmSupportsLastError`|呼び出す、Win32 呼び出しを許可する`SetLastError`属性付きメソッドから戻る前に関数。|  
|`pmCallConvMask`|予約されています。|  
|`pmCallConvWinapi`|既定のプラットフォーム呼び出し規約を使用します。 たとえば、Windows の既定値は`StdCall`とは、Windows CE .NET`Cdecl`します。|  
|`pmCallConvCdecl`|使用して、`Cdecl`呼び出し規約。 この場合、呼び出し元がスタックを消去します。 これにより、関数を呼び出す`varargs`(可変個のパラメーターを受け入れる関数)。|  
|`pmCallConvStdcall`|使用して、`StdCall`呼び出し規約。 この場合、呼び出し先がスタックを消去します。 これは、アンマネージ関数を呼び出すプラットフォーム呼び出しの既定の規則です。|  
|`pmCallConvThiscall`|使用して、`ThisCall`呼び出し規約。 この場合は、最初のパラメーターは、`this`ポインター レジスタ ECX に格納されます。 その他のパラメーターは、スタックにプッシュされます。 `ThisCall`アンマネージ DLL からエクスポートしたクラスのメソッドの呼び出しに使用呼び出し規約。|  
|`pmCallConvFastcall`|予約済み。|  
|`pmMaxValue`|予約済み。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
