---
title: 閉じるを使用し、WCF クライアントのリソースを解放する中止
description: Dispose は失敗し、ネットワークが失敗したときに例外をスローすることができます。 動作が望ましくない可能性があります。 代わりに、閉じるを使用し、ネットワークが失敗したときに、クライアントのリソースを解放する中止します。
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 58f828d9cd85806f5f04c349a7de18828ab5f6f2
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678970"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a>終了、中止のネットワーク接続が削除されるときに安全に、リソースを解放

このサンプルを使用して、`Close`と`Abort`型指定されたクライアントを使用する場合は、リソースをクリーンアップする方法。 `using`ステートメントでは、ネットワーク接続が堅牢なときに例外が発生します。 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。

> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。

このサンプルでは、C# の "using" ステートメントを型指定のあるクライアントと共に使用する際に発生する 2 つの一般的な問題と、例外が発生した後に正しくクリーンアップするコードを示します。

C# の "using" ステートメントにより `Dispose`() が呼び出されます。 これは `Close`() と同じで、ネットワーク エラーが発生したときに例外をスローする場合があります。 
  `Dispose`() への呼び出しは、"using" ブロックの閉じかっこで暗黙的に発生するので、コードを記述するユーザーとコードを読み取るユーザーの両者が、これを例外の発生元と気付かない可能性があります。 これは、アプリケーション エラーの潜在的な原因となります。

最初の問題は、次の `DemonstrateProblemUsingCanThrow` メソッドに示すように、閉じかっこで例外がスローされるとその後のコードが実行されないことです。

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

using ブロック内部からスローされる例外がない場合、または using ブロック内のすべての例外がキャッチされた場合でも、`Console.WriteLine` は発生しません。閉じかっこでの `Dispose`() の暗黙の呼び出しによって例外がスローされるためです。

2 番目の問題は、次の `DemonstrateProblemUsingCanThrowAndMask` メソッドで示すように、閉じかっこで別の例外が暗黙的にスローされる点です。

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```


  `Dispose`() は "最後の" ブロック内で発生するので、`ApplicationException`() が失敗した場合、`Dispose` は using ブロックの外側には表示されません。 外側のコードで、`ApplicationException` の発生時期を認識できるよう考慮されている場合は、この例外をマスクすると、"using" コンストラクトが問題の原因となる場合があります。

最後に、このサンプルでは、`DemonstrateCleanupWithExceptions` で例外が発生した場合に正しくクリーンアップする方法を示します。 ここでは、try/catch ブロックを使用してエラーを報告し、`Abort` を呼び出します。 参照してください、[予想例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)クライアントの呼び出しから例外をキャッチする詳細についてはサンプルです。

```csharp
try
{
    ...
    client.Close();
}
catch (CommunicationException e)
{
    ...
    client.Abort();
}
catch (TimeoutException e)
{
    ...
    client.Abort();
}
catch (Exception e)
{
    ...
    client.Abort();
    throw;
}
```

> [!NOTE]
> ステートメントと ServiceHost を使用します。多くの自己ホスト アプリケーションでは、サービスをホストして少々、ServiceHost.Close がほとんどこのようなアプリケーションを使用して、安全に使用できるように、例外がスロー ステートメントを ServiceHost と共にします。 ただし、ServiceHost.Close では `CommunicationException` がスローされる場合があることに注意してください。したがって、ServiceHost を閉じた後でアプリケーションを続行する場合は、using ステートメントを使用せずに前のパターンに従う必要があります。

このサンプルを実行すると、操作応答と例外がクライアントのコンソール ウィンドウに表示されます。

クライアント プロセスでは 3 つのシナリオが実行されます。各シナリオでは `Divide` の呼び出しが試行されます。 最初のシナリオでは、`Dispose`() からの例外のためにスキップされるコードを示します。 2 番目のシナリオでは、`Dispose`() からの例外のためにマスクされる重要な例外を示します。 3 番目のシナリオでは、正しいクリーンアップを示します。

クライアント プロセスから予期される出力は次のとおりです。

```
=
= Demonstrating problem:  closing brace of using statement can throw.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating cleanup with Exceptions.
=
Calling client.Add(0.0, 0.0);
        client.Add(0.0, 0.0); returned 0
Calling client.Divide(0.0, 0.0);
Got System.ServiceModel.CommunicationException from Divide.

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。

2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。

3. 1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
