---
title: インライン コードを使用した IIS ホスティング
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 8e401d6ce73c036188d13f40c1293abd1f0de58c
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613175"
---
# <a name="iis-hosting-using-inline-code"></a>インライン コードを使用した IIS ホスティング

このサンプルでは、インターネット インフォメーション サービス (IIS) によってホストされるサービスを実装する方法を示します。サービス コードは .svc ファイルにインラインで含まれており、必要に応じてコンパイルされます。 サービス コードは、アプリケーションの \App_Code ディレクトリにあるソース コード ファイルに直接実装するか、または \bin に配置されるアセンブリにコンパイルすることもできます。 ただし、このサンプルではこれらの手法は示しません。

> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装する一般的なサービスを示します。 このサービスは IIS によってホストされ、サービス コードは Service.svc ファイルに完全に含まれています。 サービスはホストによってアクティブ化され、このサービスに最初に送信されるメッセージによって必要に応じてコンパイルされます。 あらかじめコンパイルしておく必要はありません。 サービスは、次に示すコードで定義される `ICalculator` コントラクトを実装します。

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

このサービス実装は、計算を行い、結果を返します。

```svc
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>
```

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
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

1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。

2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。

3. ソリューションがビルドされたら、setup.bat を実行し、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] で ServiceModelSamples アプリケーションを設定します。 ServiceModelSamples ディレクトリは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] アプリケーションとして表示されます。

4. 1 つまたは複数コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。 このサービスを呼び出すことができるクライアント アプリケーションを作成する方法の例では、次を参照してください。[方法。クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)します。

## <a name="see-also"></a>関連項目

- [AppFabric のホストおよび永続化のサンプル](https://go.microsoft.com/fwlink/?LinkId=193961)
