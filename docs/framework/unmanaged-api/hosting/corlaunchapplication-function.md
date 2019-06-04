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
ms.openlocfilehash: 64527221e81569bf08a3cfd34a66681725755a55
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490535"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication 関数
指定したネットワーク パスのアプリケーションを、指定したマニフェストとその他のアプリケーション データを使用して起動します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
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
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
