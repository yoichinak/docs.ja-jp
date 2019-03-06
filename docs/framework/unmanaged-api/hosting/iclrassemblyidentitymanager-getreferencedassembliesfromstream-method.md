---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49fc3cf6aff94b5914040fba77acd0769fc73a43
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490035"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a>ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド
ポインターを取得、 [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)指定されたストリーム内のアセンブリによって参照されるアセンブリのアセンブリの id データを格納しているオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pStream`  
 [in]インターフェイス ポインターを`IStream`評価されるようにアセンブリを格納しています。  
  
 `dwFlags`  
 [in]将来の機能拡張を提供します。 CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンをサポートする唯一の値です。  
  
 `pExcludeAssembliesList`  
 [in]ポインター、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)から除外するアセンブリのアセンブリの id データを格納しているオブジェクト`ppReferenceEnum`します。  
  
 `ppReferenceEnum`  
 [out]アドレスへのポインター、`ICLRReferenceAssemblyEnum`内のアセンブリによって参照されるアセンブリのアセンブリの id データを格納しているオブジェクト`pStream`、内のアセンブリを除く`pExcludeAssembliesList`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドが正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドから E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 返された一覧から既知のアセンブリ参照のセットを除外する、呼び出し元を選択できます。 このセットがによって定義されている`pExcludeAssembliesList`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICLRAssemblyIdentityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRReferenceAssemblyEnum インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
