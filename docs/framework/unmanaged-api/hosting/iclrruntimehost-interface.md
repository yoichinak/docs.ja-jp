---
title: ICLRRuntimeHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed32fe643a7722eaf1af38e6079096194690e950
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211395"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost インターフェイス
同様の機能を提供します、 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)以下の変更をバージョン 1 では、.NET Framework で提供されるインターフェイス。  
  
-   追加、 [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)ホスト コントロールのインターフェイスを設定します。  
  
-   によって提供されるいくつかのメソッドの省略`ICorRuntimeHost`します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ExecuteApplication メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|マニフェスト ベースの ClickOnce 配置のシナリオで使用すると、新しいドメインでアクティブ化するアプリケーションを指定します。|  
|[ExecuteInAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|指定します、<xref:System.AppDomain>指定したマネージ コードを実行します。|  
|[ExecuteInDefaultAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|指定したアセンブリで指定した型の指定したメソッドを呼び出します。|  
|[GetCLRControl メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|型のインターフェイス ポインターを取得[ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)ホストは、共通言語ランタイム (CLR) の部分をカスタマイズして使用できます。|  
|[GetCurrentAppDomainId メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|数値識別子を取得、<xref:System.AppDomain>が現在実行されています。|  
|[SetHostControl メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|ホスト コントロールのインターフェイスを設定します。 呼び出す必要があります`SetHostControl`呼び出す前に`Start`します。|  
|[Start メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|プロセスに CLR を初期化します。|  
|[Stop メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|ランタイムでは、コードの実行を停止します。|  
|[UnloadAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|アンロード、<xref:System.AppDomain>指定した数値識別子に対応します。|  
  
## <a name="remarks"></a>Remarks  
 以降では、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]を使用して、 [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)へのポインターを取得するインターフェイス、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスを呼び出して、 [iclrruntimeinfo::getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)へのポインターを取得するメソッドを`ICLRRuntimeHost`します。 .NET Framework の以前のバージョンで、ホストがへのポインターを取得、`ICLRRuntimeHost`を呼び出してインスタンス[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)または[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)します。 .NET Framework version 2.0 で提供されるテクノロジのいずれかの実装を提供するには、使用する必要があります`ICLRRuntimeHost`の代わりに`ICorRuntimeHost`します。  
  
> [!IMPORTANT]
>  呼び出すのではない、[開始](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)メソッドを呼び出す前に、 [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)マニフェスト ベースのアプリケーションをアクティブ化するメソッド。 場合、`Start`メソッドが最初に、呼び出された、`ExecuteApplication`メソッドの呼び出しが失敗します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CorBindToCurrentRuntime 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
