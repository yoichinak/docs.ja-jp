---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178103"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド
指定したアセンブリのバインディング ポリシーを変更し、新しいバージョンのポリシーを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzSourceAssemblyIdentity`  
 [in]変更するアセンブリの ID。  
  
 `pwzTargetAssemblyIdentity`  
 [in]変更されたアセンブリの新しい ID。  
  
 `pbApplicationPolicy`  
 [in]変更するアセンブリのバインディング ポリシー データを格納するバッファーへのポインター。  
  
 `cbAppPolicySize`  
 [in]置き換えるバインディング ポリシーのサイズ。  
  
 `dwPolicyModifyFlags`  
 [in]リダイレクトの制御[を](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)示す値の論理 OR の組み合わせ。  
  
 `pbNewApplicationPolicy`  
 [アウト]新しいバインディング ポリシー データを格納するバッファーへのポインター。  
  
 `pcbNewAppPolicySize`  
 [イン、アウト]新しいバインディング ポリシー バッファのサイズへのポインタ。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|ポリシーは正常に変更されました。|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`または`pwzTargetAssemblyIdentity`null 参照です。|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` が小さすぎます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージ コードを実行できない状態または呼び出しを正常に処理できない状態にあります。|  
|HOST_E_TIMEOUT|通話がタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバが待機しているときにイベントがキャンセルされました。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドがE_FAILを返した後、CLR はプロセス内で使用できなくなります。 ホスト メソッドへの後続の呼び出しは、HOST_E_CLRNOTAVAILABLEを返します。|  
  
## <a name="remarks"></a>解説  
 この`ModifyApplicationPolicy`メソッドは 2 回呼び出すことができます。 最初の呼び出しでは、パラメーターに`pbNewApplicationPolicy`null 値を指定する必要があります。 この呼び出しは、 に`pcbNewAppPolicySize`必要な値を返します。 2 番目の呼び出し`pcbNewAppPolicySize`では、この値を に指定し、`pbNewApplicationPolicy`そのサイズの バッファーを指定します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRHostBindingPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
