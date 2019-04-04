---
title: 構成を使用しない AJAX サービス
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 2ea5c61ea3f0f8adcce6dc14be11a8b098c7ca0f
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332924"
---
# <a name="ajax-service-without-configuration"></a>構成を使用しない AJAX サービス
このサンプルは、Windows Communication Foundation (WCF) を使用して、任意の構成を使用せずに基本的な ASP.NET Asynchronous JavaScript and XML (AJAX) サービス (Web ブラウザー クライアントから JavaScript コードを使用してアクセスできるサービス) を作成する方法を示します。設定。 このサービスは .svc ファイルの特殊な構文を使用して AJAX エンドポイントを自動的に有効にします。  
  
 WCF での AJAX のサポートがを介して ASP.NET AJAX と共に使用するために最適化された、`ScriptManager`コントロール。 WCF を使用して ASP.NET AJAX での例は、、 [Ajax のサンプル](ajax.md)を参照してください。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、HTTP POST を使用した AJAX サービスに基づいています。 」の説明に従って、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルでは、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>サービスをホストするために使用します。  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> は、<xref:System.ServiceModel.Description.WebScriptEndpoint> をサービスに自動的に追加します。 エンドポイントに対する構成変更が不要な場合、`<system.ServiceModel>` セクションはサービスの Web.config ファイルから完全に削除できます。 Web.config ファイルには、ConfigFreeClientPage.aspx で使用される ASP.NET 設定がいくつか含まれます。 そうでない場合は、Web.config ファイル全体を削除できます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  セットアップ手順を実行することを確認します。 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2.  」の説明に従って、ソリューション ConfigFreeAjaxService.sln をビルド[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)します。  
  
3.  移動します`http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx`(はプロジェクト ディレクトリ内からブラウザーで ConfigFreeClientPage.aspx を開くしない操作を行います)。  
  
> [!NOTE]
>  このサンプルを実行する場合、IIS の ServiceModelSamples フォルダーで匿名認証と Windows 認証が同時に有効になっていないことを確認してください。 有効になっている場合は、Windows 認証を無効にしてください。 サンプルの実行が終了したら、Windows 認証を有効にし、"iisreset" を実行します。  
  
## <a name="see-also"></a>関連項目
- [基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
