---
title: ICLRRuntimeInfo インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 213fa9fda6b154d4548b4163cc7b5890bfcfb49c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186993"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo インターフェイス
バージョン、ディレクトリ、および負荷の状態を含む特定の共通言語ランタイム (CLR) に関する情報を返すメソッドを提供します。 このインターフェイスには、ランタイムを初期化せずランタイム固有の機能も提供します。 実行時の相対パスが含まれています[LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)メソッドは、ランタイム モジュール固有[GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)メソッド、およびランタイムで提供されるインターフェイスを、 [GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)メソッド。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|すべてレガシー CLR バージョン 2 のアクティブ化ポリシーを決定するためには、このランタイムをバインドします。|  
|[GetDefaultStartupFlags メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|ホスト構成ファイルの CLR スタートアップ フラグを取得します。|  
|[GetInterface メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|現在のプロセスに CLR をロードし、ランタイム、インターフェイス ポインターをなど返します[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)、 [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)と[IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)します。 このメソッドはすべて、`CorBindTo*`関数。|  
|[GetProcAddress メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|このインターフェイスに関連付けられた CLR からエクスポートされた、指定された関数のアドレスを取得します。 このメソッドは、 [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)メソッド。|  
|[GetRuntimeDirectory メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|このインターフェイスに関連付けられている CLR のインストール ディレクトリを取得します。 このメソッドは、 [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)メソッド。|  
|[GetVersionString メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|関連付けられている共通言語ランタイム (CLR) バージョン情報を取得する指定された[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイス。 このメソッドは、 [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)と[GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)メソッド。|  
|[IsLoadable メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|このインターフェイスに関連付けられているランタイムを考慮して、現在のプロセスに読み込めるかどうかを示す、プロセスに読み込まれることが既にある他のランタイム。|  
|[IsLoaded メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|CLR が関連付けられているかどうかを示す、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスが、プロセスに読み込まれます。|  
|[IsStarted メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|かどうか、CLR に関連付けられていることを示します、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスが開始されました。|  
|[LoadErrorString メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|HRESULT 値を指定したカルチャの適切なエラー メッセージに変換します。 このメソッドは、 [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)と[LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)メソッド。|  
|[LoadLibrary メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|によって表される CLR の framework ディレクトリからライブラリを読み込み、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイス。 このメソッドは、 [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)メソッド。|  
|[SetDefaultStartupFlags メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|CLR スタートアップ フラグとホスト構成ファイルを設定します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ホスト](../../../../docs/framework/unmanaged-api/hosting/index.md)
