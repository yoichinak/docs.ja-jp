---
title: 複合型を使用した AJAX サービスのサンプル
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 54d8c90f8317b69195401eda64e8a482aaf8460a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128506"
---
# <a name="ajax-service-using-complex-types-sample"></a>複合型を使用した AJAX サービスのサンプル
このサンプルでは、Windows Communication Foundation (WCF) を使用して、複合型のインスタンスを作成し、サービスとクライアントの JavaScript Object Notation (JSON) との間で送信する ASP.NET Asynchronous JavaScript and XML (AJAX) サービスを作成する方法を示します。 AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。 このサンプルでビルド、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプル。  
  
 WCF での AJAX のサポートがを介して ASP.NET AJAX と共に使用するために最適化された、<xref:System.Web.UI.ScriptManager>コントロール。 WCF を使用して ASP.NET AJAX での例は、次を参照してください。、 [AJAX のサンプル](ajax.md)します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 次のサンプルのサービスには、AJAX 固有のコードなしで WCF サービスです。 
  <xref:System.ServiceModel.Web.WebGetAttribute> 属性は適用されないため、既定の HTTP 動詞 ("POST") が使用されます。 サービスには 1 つの `DoMath` 操作があります。この操作は、`MathResult` という名前の複合型を返します。 複合型は標準のデータ コントラクト型で、AJAX 固有のコードも含まれていません。  

```csharp
[DataContract]  
public class MathResult  
{  
    [DataMember]  
    public double sum;  
    [DataMember]  
    public double difference;  
    [DataMember]  
    public double product;  
    [DataMember]  
    public double quotient;  
}  
```

 基本的な AJAX サービスのサンプルの場合と同様に、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用してサービスに AJAX エンドポイントを作成します。  
  
 クライアント Web ページ ComplexTypeClientPage.aspx には、ユーザーがクリックしたときに、サービスを呼び出す ASP.NET および JavaScript のコードが含まれています、**計算**ページ上のボタン。 サービスを呼び出すコードは、JSON 本文を構築しのような HTTP POST を使用して送信、 [AJAX サービスを使用して HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)サンプル。  
  
 サービス呼び出しに成功したら、生成された JavaScript オブジェクトのそれぞれのデータ メンバー (`sum`、`difference`、`product`、および `quotient`) にアクセスできます。  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2.  」の説明に従って、ソリューション ComplexTypeAjaxService.sln をビルド[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)します。  
  
3.  移動します`http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx`(はプロジェクト ディレクトリからブラウザーで ComplexTypeClientPage.aspx を開くしない操作を行います)。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>関連項目

- [基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
