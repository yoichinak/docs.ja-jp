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
ms.openlocfilehash: cafb85ed5f6a1245dd520ab3a5e94f95c8d37608
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762553"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo インターフェイス
バージョン、ディレクトリ、読み込み状態など、特定の共通言語ランタイム (CLR) に関する情報を返すメソッドを提供します。 このインターフェイスは、ランタイムを初期化せずにランタイム固有の機能も提供します。 これには、ランタイム相対[LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)メソッド、ランタイムモジュール固有の[GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)メソッド、および[getinterface](iclrruntimeinfo-getinterface-method.md)メソッドを使用したランタイム提供のインターフェイスが含まれます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime メソッド](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|すべてのレガシ CLR バージョン2アクティブ化ポリシーの決定にこのランタイムをバインドします。|  
|[GetDefaultStartupFlags メソッド](iclrruntimeinfo-getdefaultstartupflags-method.md)|CLR スタートアップフラグとホスト構成ファイルを取得します。|  
|[GetInterface メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|現在のプロセスに CLR を読み込み、 [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)、 [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) 、 [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md)などのランタイムインターフェイスポインターを返します。 このメソッドは、すべての関数を置き換え `CorBindTo*` ます。|  
|[GetProcAddress メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|このインターフェイスに関連付けられている CLR からエクスポートされた、指定された関数のアドレスを取得します。 このメソッドは、 [GetRealProcAddress](getrealprocaddress-function.md)メソッドよりも優先されます。|  
|[GetRuntimeDirectory メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|このインターフェイスに関連付けられている CLR のインストールディレクトリを取得します。 このメソッドは、 [Getcorsystemdirectory](getcorsystemdirectory-function.md)メソッドよりも優先されます。|  
|[GetVersionString メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|指定した[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスに関連付けられている共通言語ランタイム (CLR) のバージョン情報を取得します。 このメソッドは、 [Getrequestedruntimeinfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)および[Getrequestedruntimeinfo](getrequestedruntimeversion-function.md)メソッドを置き換えます。|  
|[IsLoadable メソッド](iclrruntimeinfo-isloadable-method.md)|このインターフェイスに関連付けられているランタイムを現在のプロセスに読み込むことができるかどうかを示します。プロセスに既に読み込まれている可能性のある他のランタイムを考慮してください。|  
|[IsLoaded メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)インターフェイスに関連付けられている CLR がプロセスに読み込まれているかどうかを示します。|  
|[IsStarted メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)インターフェイスに関連付けられている CLR が開始されているかどうかを示します。|  
|[LoadErrorString メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|HRESULT 値を、指定したカルチャの適切なエラーメッセージに変換します。 このメソッドは、 [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)メソッドと[LoadStringRCEx](loadstringrcex-function.md)メソッドよりも優先されます。|  
|[LoadLibrary メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスによって表される CLR のフレームワークディレクトリからライブラリを読み込みます。 このメソッドは、 [LoadLibraryShim](loadlibraryshim-function.md)メソッドよりも優先されます。|  
|[SetDefaultStartupFlags メソッド](iclrruntimeinfo-setdefaultstartupflags-method.md)|CLR スタートアップフラグとホスト構成ファイルを設定します。|  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](hosting-interfaces.md)
- [ホスティング](index.md)
