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
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176150"
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
|`pmNoMangle`|各メンバー名を指定どおりに使用します。|  
|`pmCharSetMask`|予約済み。|  
|`pmCharSetNotSpec`|予約済み。|  
|`pmCharSetAnsi`|マルチバイト文字として文字列をマーシャリングします。|  
|`pmCharSetUnicode`|Unicode 2 バイト文字として文字列をマーシャリングします。|  
|`pmCharSetAuto`|対象オペレーティング システムに適するように、自動的に文字列をマーシャリングします。 デフォルトは、Windows NT、Windows 2000、Windows XP、および Windows Server 2003 ファミリのユニコードです。デフォルトは、Windows 98 および Windows Me の ANSI です。|  
|`pmBestFitUseAssem`|予約済み。|  
|`pmBestFitEnabled`|ANSI 文字セットで完全に一致しない Unicode 文字の最適なマッピングを実行します。|  
|`pmBestFitDisabled`|Unicode 文字の最適なマッピングを実行しないでください。 この場合、すべてのマップできない文字は'?' に置き換えられます。|  
|`pmBestFitMask`|予約済み。|  
|`pmThrowOnUnmappableCharUseAssem`|予約済み。|  
|`pmThrowOnUnmappableCharEnabled`|相互運用マーシャラーがマップできない文字を検出したときに例外をスローします。|  
|`pmThrowOnUnmappableCharDisabled`|相互運用マーシャラーがマップできない文字を検出した場合は、例外をスローしないでください。|  
|`pmThrowOnUnmappableCharMask`|予約済み|  
|`pmSupportsLastError`|呼び出し先が、属性付きメソッド`SetLastError`から戻る前に Win32 関数を呼び出すことを許可します。|  
|`pmCallConvMask`|予約済み|  
|`pmCallConvWinapi`|既定のプラットフォーム呼び出し規約を使用します。 たとえば、Windows では既定の設定`StdCall`が、Windows CE .NET`Cdecl`では .|  
|`pmCallConvCdecl`|呼び`Cdecl`出し規約を使用します。 この場合、呼び出し元はスタックをクリーンアップします。 これにより、関数の呼`varargs`び出し (可変個のパラメーターを受け取る関数) が可能になります。|  
|`pmCallConvStdcall`|呼び`StdCall`出し規約を使用します。 この場合、呼び出し先はスタックをクリーンアップします。 これは、プラットフォーム呼び出しでアンマネージ関数を呼び出すための既定の規約です。|  
|`pmCallConvThiscall`|呼び`ThisCall`出し規約を使用します。 この場合、最初のパラメータは`this`ポインタであり、レジスタECXに格納されます。 その他のパラメーターは、スタックにプッシュされます。 呼`ThisCall`び出し規約は、アンマネージ DLL からエクスポートされたクラスのメソッドを呼び出すために使用されます。|  
|`pmCallConvFastcall`|予約済み。|  
|`pmMaxValue`|予約済み。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コルドル.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
