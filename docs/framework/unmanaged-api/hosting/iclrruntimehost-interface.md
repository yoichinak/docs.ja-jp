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
ms.openlocfilehash: 0f159c0b57f2087b608fac8cbc9b9c64ceb063a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965991"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost インターフェイス
.NET Framework バージョン1で提供される[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)インターフェイスと同様の機能を提供します。次の変更点があります。  
  
- ホストコントロールインターフェイスを設定するための[Sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)メソッドの追加。  
  
- によっ`ICorRuntimeHost`て提供されるいくつかのメソッドの省略。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ExecuteApplication メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|新しいドメインでアクティブ化するアプリケーションを指定するために、マニフェストベースの ClickOnce 配置シナリオで使用されます。|  
|[ExecuteInAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<xref:System.AppDomain>指定したマネージコードを実行するを指定します。|  
|[ExecuteInDefaultAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|指定したアセンブリ内で、指定した型の指定したメソッドを呼び出します。|  
|[GetCLRControl メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|ホストが共通言語ランタイム (CLR) の側面をカスタマイズするために使用できる、 [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)型のインターフェイスポインターを取得します。|  
|[GetCurrentAppDomainId メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|現在実行中のの<xref:System.AppDomain>数値識別子を取得します。|  
|[SetHostControl メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|ホストコントロールインターフェイスを設定します。 を呼び出す`SetHostControl` `Start`前に、を呼び出す必要があります。|  
|[Start メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|CLR をプロセスに初期化します。|  
|[Stop メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|ランタイムによるコードの実行を停止します。|  
|[UnloadAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|指定した数値識別子に対応するをアンロードします。<xref:System.AppDomain>|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework 4 以降では、 [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)インターフェイスを使用して[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスへのポインターを取得し、 [ICLRRuntimeInfo:: getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)メソッドを呼び出して、へ`ICLRRuntimeHost`のポインターを取得します。 以前のバージョンの .NET Framework では、ホストは`ICLRRuntimeHost` [corbindtoruntimeex](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)または[corbindtoの entruntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)を呼び出すことによって、インスタンスへのポインターを取得します。 .NET Framework バージョン2.0 で提供されるテクノロジの実装を提供するには、の`ICLRRuntimeHost` `ICorRuntimeHost`代わりにを使用する必要があります。  
  
> [!IMPORTANT]
> マニフェストベースのアプリケーションをアクティブ化するには、 [Executeapplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)メソッドを呼び出す前に[Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)メソッドを呼び出さないでください。 メソッドが最初`ExecuteApplication`に呼び出された場合、メソッドの呼び出しは失敗します。 `Start`  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CorBindToCurrentRuntime 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
