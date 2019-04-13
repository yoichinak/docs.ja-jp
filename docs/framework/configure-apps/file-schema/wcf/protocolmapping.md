---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: e26044340bda84fe38b7e286edf833affa94b86c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118216"
---
# <a name="protocolmapping"></a>\<protocolMapping >
トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と WCF バインディング間の既定のプロトコル マッピングのセットを定義する構成セクションを表します。 実行時に既定のエンドポイントを作成するときに、Windows Communication Foundation (WCF) が構成済みのマッピングではされ、特定に使用するバインディングをベース アドレスを決定します。  
  
[**\<system.serviceModel>**](system-servicemodel.md)  
&nbsp;&nbsp;**\<protocolMapping >**  
  
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
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と WCF バインディング間の既定のプロトコル マッピングが含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|すべての WCF 構成要素のルート要素です。|  
  
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
