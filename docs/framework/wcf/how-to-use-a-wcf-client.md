---
title: '方法: Windows Communication Foundation のクライアントを使用してください。'
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 780a51e3e0f61f292c997202614e43a85dd90820
ms.sourcegitcommit: a532e8314c3a4b5b039656567fedff9787a31957
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57250924"
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>方法: Windows Communication Foundation のクライアントを使用してください。

これは、基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な 6 つのタスクの最後のタスクです。 6 つのすべてのタスクの概要については、「[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。

Windows Communication Foundation (WCF) プロキシを作成および構成するとクライアント インスタンスを作成して、クライアント アプリケーションをコンパイルし、WCF サービスと通信するために使用します。 このトピックでは、インスタンス化し、WCF クライアントを使用して手順を説明します。 この手順は、次の 3 つの手順で構成されます。

1.  WCF クライアントをインスタンス化します。

2.  生成されたプロキシからサービス操作を呼び出します。

3.  操作の呼び出しが完了したらクライアントを閉じます。

## <a name="use-a-windows-communication-foundation-client"></a>Windows Communication Foundation クライアントを使用します。

GettingStartedClient プロジェクトの Program.cs ファイルまたは Program.vb ファイルを開き、既存のコードを次のコードで置き換えます。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            //Step 3: Closing the client gracefully closes the connection and cleans up resources.
            client.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClientVB2.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy
        Dim Client As New CalculatorClient()

        'Step 2: Call the service operations.
        'Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        'Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        'Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        'Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Closing the client gracefully closes the connection and cleans up resources.
        Client.Close()

        Console.WriteLine()
        Console.WriteLine("Press <ENTER> to terminate client.")
        Console.ReadLine()

    End Sub

End Module
```

通知、`using`または`Imports`をインポートするステートメント、`GettingStartedClient.ServiceReference1`します。 これにより、インポートによって生成されたコード**サービス参照の追加**Visual Studio でします。 コードは、WCF プロキシをインスタンス化し、電卓サービスによって公開されるサービス操作の各呼び出しが、プロキシを閉じるし、終了します。

これで、チュートリアルは終了です。 サービス コントラクトの定義、サービス コントラクトの実装、WCF プロキシの生成、WCF クライアント アプリケーションの構成、そしてプロキシの使用によるサービス操作の呼び出しを行いました。 アプリケーションをテストするには、まず、サービスを開始し、GettingStartedClient を実行し、GettingStartedHost を実行します。

GettingStartedHost からの出力は、次のようになります。

```text
The service is ready.
Press <ENTER> to terminate service.

Received Add(100,15.99)
Return: 115.99
Received Subtract(145,76.54)
Return: 68.46
Received Multiply(9,81.25)
Return: 731.25
Received Divide(22,7)
Return: 3.14285714285714
```

GettingStartedClient からの出力は、次のようになります。

```text
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

## <a name="see-also"></a>関連項目

- [クライアントを構築する](../../../docs/framework/wcf/building-clients.md)
- [方法: クライアントを作成します。](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)
- [基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)
- [方法: 双方向コントラクトを作成します。](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [方法: Access Services と双方向コントラクト](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [はじめに](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)
