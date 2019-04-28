---
title: <add> の <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 85d09c920de2ca1ab4971551ff98ea58c4492f44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704493"
---
# <a name="add-of-protocolmapping"></a>\<追加 > の\<protocolMapping >
トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と Windows Communication Foundation (WCF) バインドの間の既定のプロトコル マッピングを表します。 実行時に既定のエンドポイントを作成するときに、WCF は構成済みのマッピングではされ、特定に使用するバインディングをベース アドレスを決定します。  
  
 \<system.serviceModel>  
\<protocolMapping >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|要素|説明|  
|-------------|-----------------|  
|バインド|既定のエンドポイントを作成するときにエンドポイントに使用されるバインディングの種類を指定する文字列。|  
|bindingConfiguration|参照されるバインディング構成セクションの名前を指定する文字列。|  
|scheme|既定のエンドポイントに使用されるトランスポート プロトコル スキーム。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<protocolMapping>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と Windows Communication Foundation (WCF) バインドの間の既定のプロトコル マッピングを定義するための構成セクションを表します。|  
  
## <a name="example"></a>例  
 次の構成例は、machine.config ファイル内の既定のプロトコル マッピングを示しています。 machine.config ファイルを変更することで、既定のマッピングをコンピューター レベルでオーバーライドできます。 または、アプリケーションのスコープ内だけでオーバーライドする場合は、アプリケーション構成ファイルのこのセクションをオーバーライドし、各プロトコル スキームのマッピングを変更できます。  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
