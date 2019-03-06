---
title: ICLRRuntimeInfo::SetDefaultStartupFlags メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 440f2f7c542c697b3d817c988211303c60073979
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492362"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a>ICLRRuntimeInfo::SetDefaultStartupFlags メソッド
スタートアップ フラグとランタイムの起動に使用されるホストの構成ファイルを設定します。 このメソッドの使用よりも優先されます、`startupFlags`パラメーター、 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)と[CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)関数。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwStartupFlags`  
 [in]設定するホストのスタートアップ フラグ。 使用したのと同じフラグを使用して、 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)と[CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)関数。  
  
 `pwzHostConfigFile`  
 [in]設定するホストの構成ファイルのディレクトリ パス。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT を返します。 メソッドの失敗を示す HRESULT エラーとします。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
  
## <a name="remarks"></a>Remarks  
 マルチ スレッドのホストには、このメソッドの呼び出しを同期する必要があります。 それ以外の場合、スレッド A が呼び出すことができます、`SetStartupFlags`スレッド B への呼び出しの完了後に、`SetStartupFlags`スレッド B が、ランタイムを開始する前にします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICLRRuntimeInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
