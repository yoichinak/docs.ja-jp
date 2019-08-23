---
title: コンカレンシー
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: ab1cab4cf2c9fb8902eef321bfa7b1a610376771
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969040"
---
# <a name="concurrency"></a>コンカレンシー
コンカレンシーのサンプルでは、<xref:System.ServiceModel.ServiceBehaviorAttribute> を <xref:System.ServiceModel.ConcurrencyMode> 列挙体と共に使用する方法を示します。この列挙体は、サービスのインスタンスがメッセージを順番に処理するか、または同時に処理するかを制御します。 このサンプルは、 `ICalculator`サービスコントラクトを実装する[はじめに](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいています。 このサンプルでは、`ICalculatorConcurrency` から継承される新しいコントラクト `ICalculator` を定義します。これによって、サービスのコンカレンシーの状態を検査するための 2 つの操作が追加されます。 コンカレンシー設定を変更してから、クライアントを実行して動作の変更を確認します。  
  
 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 選択可能なコンカレンシー モードは次の 3 つです。  
  
- `Single`:各サービスインスタンスは、一度に1つのメッセージを処理します。 これが既定のコンカレンシー モードです。  
  
- `Multiple`:各サービスインスタンスは、複数のメッセージを同時に処理します。 このコンカレンシー モードを使用するには、サービスの実装がスレッドセーフである必要があります。  
  
- `Reentrant`:各サービスインスタンスは一度に1つのメッセージを処理しますが、再入可能な呼び出しを受け入れます。 サービスがこの呼び出しを受け入れるのは、コール アウトするときだけです。再入は、 [ConcurrencyMode](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md)サンプルで説明されています。  
  
 コンカレンシーの使用は、インスタンス化モードに関連します。 <xref:System.ServiceModel.InstanceContextMode.PerCall> インスタンス化では、各メッセージが新しいサービス インスタンスによって処理されるため、コンカレンシーは関係しません。 <xref:System.ServiceModel.InstanceContextMode.Single> インスタンス化では、<xref:System.ServiceModel.ConcurrencyMode.Single> と <xref:System.ServiceModel.ConcurrencyMode.Multiple> のいずれかのコンカレンシーが関係します。これは 1 つのインスタンスがメッセージを順番に処理するか、同時に処理するかによって決まります。 <xref:System.ServiceModel.InstanceContextMode.PerSession> インスタンス化では、どのコンカレンシー モードも関係する可能性があります。  
  
 サービス クラスは、`[ServiceBehavior(ConcurrencyMode=<setting>)]` 属性を使用してコンカレンシー動作を指定します。次のサンプル コードを参照してください。 行のコメント化を変更して、`Single` および `Multiple` のコンカレンシー モードをそれぞれ試してみてください。 コンカレンシー モードを変更したら、サービスを再ビルドする必要があります。  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 サンプルの既定の設定では、<xref:System.ServiceModel.ConcurrencyMode.Multiple> インスタンス化と <xref:System.ServiceModel.InstanceContextMode.Single> コンカレンシーが使用されます。 クライアント コードは、非同期プロキシを使用するように変更されています。 これにより、クライアントはサービスを呼び出した後に、応答を待たずに次の呼び出しを行うことができます。 サービスのコンカレンシー モードの動作の違いを観察してください。  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 実行中のサービスのコンカレンシー モードが表示され、各操作が呼び出され、その後で操作数が表示されます。 コンカレンシー モードが `Multiple` の場合、結果が返される順序は呼び出された順序とは異なります。サービスは複数のメッセージを同時に実行するからです。 コンカレンシー モードを `Single` に変更すると、結果は呼び出された順序どおりに返されます。サービスは各メッセージを順次処理するからです。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。  
  
2. Svcutil.exe を使用してプロキシクライアントを生成する場合は、 `/async`オプションが含まれていることを確認してください。  
  
3. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4. サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
