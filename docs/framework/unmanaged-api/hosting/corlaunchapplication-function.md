---
title: CorLaunchApplication 関数
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e10a92b1748fcdf518fa68cb7054731f4511396b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487188"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication 関数
指定したネットワーク パスのアプリケーションを、指定したマニフェストとその他のアプリケーション データを使用して起動します。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwClickOnceHost`  
 [in]値、 [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)が起動して、アプリケーション ホストの種類を指定する列挙体。  
  
 `pwzAppFullName`  
 [in]起動しているアプリケーションの完全名。  
  
 `dwManifestPaths`  
 [in]アプリケーションのマニフェストのパスの数。  
  
 `ppwzManifestPaths`  
 [in]起動しているアプリケーションのマニフェストへのパスを指定の文字列の配列。  
  
 `dwActivationData`  
 [in]起動しているアプリケーションのデータ項目をアクティブ化の数。  
  
 `ppwzActivationData`  
 [in]起動しているアプリケーションのライセンス認証データ項目は、それぞれの文字列の配列。  
  
 `lpProcessInformation`  
 [out]これで、アプリケーションが読み込まれたプロセスに関する情報へのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
