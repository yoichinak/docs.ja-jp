---
title: CreateAssemblyCache 関数
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6327c9d7dee548957a569b587faefe3d6d9cb1b9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497770"
---
# <a name="createassemblycache-function"></a>CreateAssemblyCache 関数
新しいポインターを取得します。 [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)グローバル アセンブリ キャッシュを表すインスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppAsmCache`  
 [out]返された`IAssemblyCache`ポインター。  
  
 `dwReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `dwReserved` 0 (ゼロ) である必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IAssemblyCache インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [グローバル アセンブリ キャッシュ](../../../../docs/framework/app-domains/gac.md)
