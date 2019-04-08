---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: ca6d401109d14ce11dcd40c393cd079170e4d20d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259871"
---
# <a name="webhttp"></a>\<webHttp>
この要素は、構成によってエンドポイントに <xref:System.ServiceModel.Description.WebHttpBehavior> を指定します。 この動作は、組み合わせて使用する場合、 [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準バインディングにより、Windows Communication Foundation (WCF) サービスの Web プログラミング モデル。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<endpointBehaviors>  
\<behavior>  
\<webHttp>  
  
## <a name="syntax"></a>構文  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|このプロパティが `true` に設定されている場合は、使用する最適な形式が WCF インフラストラクチャで決定されます。 形式の自動選択は、既定で、下位互換性のために無効になっています。 形式の自動選択は、プログラムで有効にすることも、構成ファイルを使用して有効にすることもできます。|  
|defaultBodyStyle|返されたメッセージの既定の本文のスタイルを指定します。 詳細については、<xref:System.ServiceModel.Web.WebMessageBodyStyle>と[WCF Web HTTP 書式](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)を参照してください。|  
|defaultOutgoingResponseFormat|メッセージの既定の送信応答形式を指定します。 詳細については、[WCF Web HTTP 書式](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)を参照してください。|  
|faultExceptionEnabled|内部サーバー エラー (HTTP ステータス コード: 500) が発生したときに FaultException が生成されるかどうかを指定するフラグを取得または設定します。|  
|helpEnabled| ヘルプ ページが有効かどうかを示す値を取得または設定します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|エンドポイントの動作のセットを指定します。|  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [AJAX の統合と JSON のサポート](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
