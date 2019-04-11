---
title: ICLRMetaHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1b189b79a02f04b7f795ff2524441f12b053cec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143950"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost インターフェイス
そのバージョン番号に基づく共通言語ランタイム (CLR) の特定のバージョンを返す、インストールされている Clr のすべてを一覧表示、指定されたプロセスに読み込まれるすべてのランタイムの一覧で、アセンブリをコンパイル、プロセスを終了するために使用する CLR のバージョンを検出するメソッドを提供します。ランタイムがクリーン シャット ダウンとクエリのレガシ API バインドします。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|含む、有効な列挙体を返します[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)コンピューターにインストールされている CLR のバージョンごとにインターフェイス ポインター。|  
|[EnumerateLoadedRuntimes メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|含む、有効な列挙体を返します[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)特定のプロセスに読み込まれる各 CLR 用のインターフェイス ポインター。 このメソッドは[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)します。|  
|[ExitProcess メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|すべての読み込まれたランタイムを適切にシャット ダウンしようとしてのプロセスを終了します。 も優先されます、 [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)関数。|  
|[GetRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|取得、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)特定の CLR バージョンに対応するインターフェイス。 このメソッドは、 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)で使用される関数、 [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)フラグ。|  
|[GetVersionFromFile メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|指定されたファイル パスから、アセンブリの元の .NET Framework コンパイル バージョン (メタデータに格納されている) を取得します。 このメソッドは[GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)します。|  
|[QueryLegacyV2RuntimeBinding メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|レガシ アクティブ化ポリシーが関連付けられて、例を使用してランタイムを表すインターフェイスを返します、`useLegacyV2RuntimeActivationPolicy`属性を[ \<startup > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)ダイレクトを使用して、構成ファイルのエントリレガシ アクティブ化 Api、または呼び出すことによって、 [iclrruntimeinfo::bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)メソッド。|  
|[RequestRuntimeLoadedNotification メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|CLR バージョンは、最初に読み込まれたが、開始していない場合に、指定した関数ポインターへのコールバックを保証します。 このメソッドは[LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスのインスタンスを取得する唯一の方法は、呼び出すことによって、 [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)関数の次のようにします。  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ホスト](../../../../docs/framework/unmanaged-api/hosting/index.md)
