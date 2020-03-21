---
title: 複数のコントラクト
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: ed59803b867dfe7994aceea010aa656c53927a0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144345"
---
# <a name="multiple-contracts"></a>複数のコントラクト
この複数のコントラクトのサンプルでは、複数のコントラクトを 1 つのサービスに実装する方法と、実装された各コントラクトと通信を行うためにエンドポイントを構成する方法を示します。 このサンプルは、[作業の開始に](../../../../docs/framework/wcf/samples/getting-started-sample.md)基づいています。 サービスは、`ICalculator` コントラクトおよび `ICalculatorSession` コントラクトという、2 つのコントラクトを定義するように変更されています。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービス クラスは、`ICalculator` と `ICalculatorSession` コントラクトの両方を実装しています。 いずれかのコントラクトでセッションが必要なので、サービスは <xref:System.ServiceModel.InstanceContextMode.PerSession> インスタンス モードを使用して、セッションの有効期間中、状態を保持します。  
  
 サービス構成は、各コントラクトを公開する 2 つのエンドポイントを定義するように変更されています。 `ICalculator` エンドポイントは、`basicHttpBinding` を使用してベース アドレスで公開されます。 `ICalculatorSession` エンドポイントは、`wsHttpBinding` 属性が `bindingConfiguration` に設定された `BindingWithSession` を使用して、ベース アドレスまたはセッションで公開されます。次のサンプル構成を参照してください。  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 生成されたクライアント コードには、元の `ICalculator` コントラクトと新しい `ICalculatorSession` コントラクトの両方のクライアント クラスが含まれます。 クライアント構成とコードは、適切なサービス エンドポイントで各コントラクトと通信するように変更されています。  
  
 クライアントは Windows コンソール アプリケーション (.exe) です。 サービスは、インターネット インフォメーション サービス (IIS) によってホストされます。  
  
 クライアント コンソール ウィンドウには、最初に基本のエンドポイント、次にセキュリティで保護されたエンドポイントの順に、各エンドポイントに送信された操作が表示されます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
