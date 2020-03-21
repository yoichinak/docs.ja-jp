---
title: WS 信頼できるセッション
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 8898dfedc6ba7deceb5a6e6856b7c7e6ad79d047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143500"
---
# <a name="ws-reliable-session"></a>WS 信頼できるセッション
このサンプルでは、信頼できるセッションの使用方法を示します。 信頼できるセッションは、信頼できるメッセージとセッションをサポートします。 信頼できるメッセージは、エラー時に通信を再試行するほか、メッセージの順次到着などの配信の保証を指定できるようにします。 セッションでは、呼び出し間でクライアントの状態が保持されます。 サンプルでは、クライアントの状態を保持するセッションを実装し、配信順序を保証することを指定します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 このサンプルは、電卓サービスを実装する[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいています。 信頼できるセッション機能は、クライアントとサービスのアプリケーション構成ファイルで有効化され、構成されています。  
  
 このサンプルでは、サービスはインターネット インフォメーション サービス (IIS) によってホストされており、クライアントはコンソール アプリケーション (.exe) です。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、`wsHttpBinding` を使用しています。 バインディングは、クライアントとサービスの両方の構成ファイルに指定されます。 バインディングの種類はエンドポイント要素の `binding` 属性に指定します。次のサンプル構成を参照してください。  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 エンドポイントには、"Binding1" という名前のバインド構成を参照する `bindingConfiguration` 属性が含まれます。 バインディング構成では`enabled`[\<、reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)の属性を に設定することで`true`、信頼できるセッションを有効にします。 順序付きセッションの配信の保証は、ordered 属性を `true` または `false` に設定することによって制御されます。 既定では、 `true`です。  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 サービス実装クラスは、クライアントごとに個別のクラスのインスタンスをインスタンス化して保持する <xref:System.ServiceModel.InstanceContextMode.PerSession> を実装します。次のサンプル コードを参照してください。  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 次のコマンドASP.NET使用して、4.0 をインストールします。  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
3. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。  
