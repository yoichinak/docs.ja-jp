---
title: 予期される例外
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: f250e526b528adf0b67365ceb07f13e4087d773d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144710"
---
# <a name="expected-exceptions"></a>予期される例外
このサンプルでは、型指定のあるクライアントを使用する際に、予期される例外をキャッチする方法を示します。 このサンプルは、電卓サービスを実装する[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいています。 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、正しいプログラムが処理する必要のある `TimeoutException` および `CommunicationException` という 2 種類の予期される例外を、キャッチして処理する方法を示します。  
  
 Windows 通信基盤 (WCF) クライアント上の通信メソッドからスローされる例外は、予期されるまたは予期しないのいずれかです。 予期しない例外には、`OutOfMemoryException` などの致命的なエラーや、`ArgumentNullException` や `InvalidOperationException` などのプログラミング エラーが含まれます。 通常、予期しないエラーを処理する便利な方法はありませんので、通常は WCF クライアント通信メソッドを呼び出すときにキャッチしないでください。  
  
 WCF クライアントの通信メソッドから期待される例外には`TimeoutException`、 `CommunicationException`、および の派生`CommunicationException`クラスが含まれます。 これらは、WCF クライアントを中止し、通信障害を報告することによって安全に処理できる通信中の問題を示します。 どのアプリケーションでも外部要因によってこうしたエラーが発生する可能性があるので、正しいアプリケーションはこのようなエラーをキャッチし、発生した場合には回復させる必要があります。  
  
 `CommunicationException` の派生クラスには、クライアントがスローできるものがいくつかあります。 状況によっては、アプリケーションでこれらのサブクラスをキャッチして特別な処理を行うこともできます。しかし、それ以外の場合は `CommunicationException` として処理する必要があります。 この処理は、より具体的な例外の種類を最初にキャッチし、後の catch 句で `CommunicationException` をキャッチすることによって実現できます。  
  
 クライアントの通信メソッドを呼び出すコードでは、`TimeoutException` と `CommunicationException` をキャッチする必要があります。 こうしたエラーの処理方法の 1 つに、クライアントを中止して通信エラーを報告するという方法があります。  
  
```csharp
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 予期される例外が発生した場合、それ以降、クライアントを使用できる場合もできない場合もあります。 クライアントがそのまま使用可能かどうかを確認するには、`State` プロパティが `CommunicationState`.Opened であることを確認してください。 Opened の場合は、そのまま使用できます。 それ以外の場合は、クライアントを中止してすべての参照を解放する必要があります。  
  
> [!CAUTION]
> 一般に、セッションを持つクライアントは、例外発生後に使用できなくなり、セッションを持たないクライアントは、例外発生後も使用可能なままです。 ただし、どちらも必ずそうなるとは限りません。したがって、例外発生後も引き続きクライアントを使用する場合は、アプリケーションで `State` プロパティをチェックし、クライアントが Opened 状態のままであることを検証する必要があります。  
  
 このサンプルを実行すると、操作応答と例外がクライアントのコンソール ウィンドウに表示されます。  
  
 クライアント プロセスでは 2 つのシナリオが実行されます。各シナリオでは、`Add`、`Divide` の順に呼び出しが試行されます。 最初のシナリオでは、`Divide` を呼び出す前にクライアントを中止することによってネットワーク問題をシミュレートします。 2 番目のシナリオでは、メソッドを完了できないようにタイムアウト値をごく短く設定することによって、タイムアウトを発生させます。 クライアント プロセスから予期される出力は次のとおりです。  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
