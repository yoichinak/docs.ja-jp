---
title: ASM_CACHE_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 619643eb50abc75fd10d59b38767013b2617c8cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077778"
---
# <a name="asmcacheflags-enumeration"></a>ASM_CACHE_FLAGS 列挙型
表されるアセンブリのソースを示す[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)グローバル アセンブリ キャッシュにします。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|Ngen.exe を使用して、プリコンパイル済みアセンブリのキャッシュを列挙します。|  
|`ASM_CACHE_GAC`|グローバル アセンブリ キャッシュを列挙します。|  
|`ASM_CACHE_DOWNLOAD`|オンデマンドでダウンロードされたまたはシャドウ コピーされているが、アセンブリを列挙します。|  
|`ASM_CACHE_ROOT`|示します、 [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)関数は、共通言語ランタイム (CLR) バージョン 2.0 のグローバル アセンブリ キャッシュにパスを返す必要があります。 呼び出しのコンテキストでのみ意味のある[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)します。|  
|`ASM_CACHE_ROOT_EX`|示します、 [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)関数は、グローバル アセンブリ キャッシュにパスを CLR version 4 に返す必要があります。 呼び出しのコンテキストでのみ意味のある[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetCachePath 関数](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)
- [IAssemblyCacheItem インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
- [fusion 列挙体](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
