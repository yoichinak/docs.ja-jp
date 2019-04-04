---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 692c4cf6688bfc2f9b99f065f4b16711f7f08063
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412046"
---
# <a name="nettcp"></a>\<net.tcp>
複数のプロセスが同じ TCP ポートを共有できる NET.TCP ポート共有サービスの構成設定を指定します。  
  
 \<system.serviceModel.activation>  
\<net.tcp>  
  
## <a name="syntax"></a>構文  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`listenBacklog`|共有接続から受け入れられたが、Windows Communication Foundation (WCF) サービスにまだディスパッチされていない最大の未処理の接続を指定する整数。 既定値は 10 です。|  
|`maxPendingAccepts`|整数は、共有サービスの待機エンドポイントで同時に受け入れる未処理のスレッドの最大数を示しています。 既定値は 2 です。|  
|`MaxPendingConnections`|アプリケーションによる受け入れをリスナーで待機できる最大接続数。 このクォータ値を超過すると、新規の受信接続は受け入れられるのを待機せずに切断されます。 メッセージ セキュリティのような接続機能では、クライアントは複数の接続を開くことがあります。 このクォータ値を設定する場合、サービス管理者はこのような追加の接続も考慮する必要があります。 既定値は 10 です。|  
|`receiveTimeout`|フレーム データを読み取り、基礎となる接続から接続ディスパッチを実行するタイムアウトを指定する <xref:System.TimeSpan> です。 既定値は "00:00:10" です。|  
|`teredoEnabled`|ポート共有サービスが Microsoft Teredo サービスを使用して WCF サービスに代わって TCP ポートでリッスンするかどうかを示すブール値。 既定値は `false` です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|格納する構成要素のコレクションを`securityIdentifier`属性を WCF サービスをホストし、共有サービスへの接続アクセスが許可されるプロセスのユーザー アカウントを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel.activation >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|リスナー プロセス SMSvcHost.exe の設定が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 ポート共有の詳細については、[Net.TCP ポート共有](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)を参照してください。 ポート共有サービスを構成する方法については、[Net.TCP ポート共有サービスを構成する](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Net.TCP ポート共有](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Net.TCP ポート共有サービスを構成する](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
