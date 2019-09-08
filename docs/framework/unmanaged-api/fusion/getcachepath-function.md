---
title: GetCachePath 関数
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1c28f32a4b24393483241bd2d7d6f550b8b65ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796908"
---
# <a name="getcachepath-function"></a>GetCachePath 関数
指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwCacheFlags`  
 からキャッシュされたアセンブリのソースを示す[ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md)値です。  
  
 `pwzCachePath`  
 入出力パスへの返されたポインター。  
  
 `pcchPath`  
 [入力、出力]要求された最大`pwzCachePath`長。戻り値は、の実際の`pwzCachePath`長さ。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ASM_CACHE_FLAGS 列挙型](asm-cache-flags-enumeration.md)
- [Fusion グローバル静的関数](fusion-global-static-functions.md)
