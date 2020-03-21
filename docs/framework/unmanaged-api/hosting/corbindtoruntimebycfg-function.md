---
title: CorBindToRuntimeByCfg 関数
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: 4fbc6e7ea531f65a6b1cd0ec93f4847ab8e4fe83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178242"
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg 関数
XML ファイルから読み取られたバージョン情報を使用して、共通言語ランタイム (CLR) をプロセスに読み込みます。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pCfgStream`  
 [in]XML ファイルを`IStream`読み取るオブジェクトへのポインター。  
  
 `reserved`  
 [in]将来の使用のために予約されています。 値として 0 (ゼロ) を使用します。  
  
 `startupFlags`  
 [in]CLR のスタートアップ動作を指定する[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列挙体の値。  
  
 `rclsid`  
 [in]`CLSID`インターフェイス[を実装](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)するコクラスの[。](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。  
  
 `riid`  
 [in]`ICorRuntimeHost`または`IID``ICLRRuntimeHost`インターフェイスのいずれか。 サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。  
  
 `ppv`  
 [アウト]返されたインターフェイスのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  
 XML ファイルの形式は、標準アプリケーション構成ファイルをモデルにしています。 XML ファイルの詳細については、「[構成ファイル スキーマ](../../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CorBindToCurrentRuntime 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeEx 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
