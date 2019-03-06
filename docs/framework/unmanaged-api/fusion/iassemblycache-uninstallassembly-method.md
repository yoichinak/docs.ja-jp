---
title: IAssemblyCache::UninstallAssembly メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5347d25f3fe1d5136917564b1fed24df5df0449c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468079"
---
# <a name="iassemblycacheuninstallassembly-method"></a>IAssemblyCache::UninstallAssembly メソッド
指定したアセンブリをグローバル アセンブリ キャッシュからアンインストールします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwFlags`  
 [in]ものがありますで定義されているフラグ。  
  
 `pszAssemblyName`  
 [in]アンインストールするアセンブリの名前。  
  
 `pRefData`  
 [in]A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)アセンブリのインストール データを含む構造体。  
  
 `pulDisposition`  
 [out] 省略可能ものがありますで定義されている配置の値の 1 つ。 使用可能な値を以下に示します。  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IAssemblyCache インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
