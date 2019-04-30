---
title: ICLRMetaHost::GetRuntime メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b71d0f29d770b2722b0dfaabc8b9667e524c99e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984608"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime メソッド
取得、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)共通言語ランタイム (CLR) の特定のバージョンに対応するインターフェイス。 このメソッドは、 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)で使用される関数、 [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)フラグ。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzVersion`  
 [in]形式で、メタデータに格納されている .NET Framework のコンパイル バージョン"v*A*.*B*[.*X*]"。 *A*、 *B*、および*X*はメジャー バージョン、マイナー バージョン、およびビルド番号に対応する 10 進数。  
  
> [!NOTE]
>  C:\Windows\Microsoft.NET\Framework または C:\Windows\Microsoft.NET\Framework64 で表示される、このパラメーターは .NET Framework のバージョンのディレクトリ名に一致する必要があります。  
  
 例の値は、"v1.0.3705"、"v1.1.4322"、"v2.0.50727"および"v4.0 です。*X*"ここで、 *X*インストールされているビルドの数によって異なります。 "V"プレフィックスが必要です。  
  
 `riid`  
 [in]必要なインターフェイスの識別子。 現時点では、このパラメーターの唯一の有効な値は、IID_ICLRRuntimeInfo です。  
  
 `ppRuntime`  
 [out]ポインター、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)要求されたランタイムに対応するインターフェイス。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pwzVersion` または `ppRuntime` が null です。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドとやり取り一貫して従来のインターフェイスなど、 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)インターフェイスおよび従来の関数など、非推奨`CorBindTo*`関数 (を参照してください[非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) API をホストしている .NET Framework 2.0 で)。 レガシ API で読み込まれたランタイムは、新しい API に表示されると、新しい API が読み込まれているランタイムがレガシ API に表示されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMetaHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [非推奨の CLR のホスト インターフェイスおよびコクラス](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
