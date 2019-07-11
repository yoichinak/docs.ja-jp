---
title: CorCallingConvention 列挙型
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 576fb8632818a6b8ffc3e2c0acc50eaafd074de3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766965"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention 列挙型
マネージド コードで作成される呼び出し規則のタイプを記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|既定の呼び出し規約を示します。|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|メソッドが変数の数のパラメーターを受け取ることを示します。|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|フィールドへの呼び出しがあることを示します。|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|ローカル メソッド呼び出しがあることを示します。|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|プロパティへの呼び出しがあることを示します。|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|呼び出しが管理対象であることを示します。|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|ジェネリック メソッドのインスタンス化を示します。|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|可変個のパラメーターを受け取るメソッドへの 64 ビット PInvoke 呼び出しを示します。|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|無効な 4 ビット値をについて説明します。|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|下位 4 ビットで、呼び出し規則が記述されていることを示します。|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|最上位ビットを記述していることを示します、`this`パラメーター。|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|示します、`this`パラメーターは、署名には明示的に記述します。|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|型引数の明示的な数のジェネリック メソッドのシグネチャを示します。 これには、通常のパラメーター カウントよりも前します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
