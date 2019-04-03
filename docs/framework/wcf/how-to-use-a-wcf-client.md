---
title: 'チュートリアル: Windows Communication Foundation クライアントを使用します。'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 4d883277f795ea84c59aee91ffcb9b9802b0933b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411721"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>チュートリアル: Windows Communication Foundation クライアントを使用します。

このチュートリアルでは、基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な 5 つのタスクの最後のタスクについて説明します。 チュートリアルの概要については、[チュートリアル。Windows Communication Foundation アプリケーションの概要](getting-started-tutorial.md)を参照してください。

作成、Windows Communication Foundation (WCF) プロキシを構成したら後、は、クライアント インスタンスを作成し、クライアント アプリケーションをコンパイルします。 使用する WCF サービスと通信します。 

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> - WCF クライアントを使用するコードを追加します。
> - WCF クライアントをテストします。

## <a name="add-code-to-use-the-wcf-client"></a>WCF クライアントを使用するコードを追加します。

クライアント コードは、次の手順を行います。
- WCF クライアントをインスタンス化します。
- 生成されたプロキシからサービス操作を呼び出します。
- 操作の呼び出しが完了した後は、クライアントを閉じます。

開く、 **Program.cs**または**Module1.vb**ファイルから、 **GettingStartedClient**プロジェクトし、そのコードを次のコードに置き換えます。

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

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
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
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

通知、 `using` (ビジュアルのC#) または`Imports`(Visual Basic) のインポート ステートメント`GettingStartedClient.ServiceReference1`します。 このステートメントで Visual Studio が生成されたコードをインポートする、**サービス参照の追加**関数。 コードでは、WCF プロキシをインスタンス化し、電卓サービスを公開するサービス操作の各を呼び出します。 プロキシを終了し、プログラムが終了します。

## <a name="test-the-wcf-client"></a>WCF クライアントをテストします。

### <a name="test-the-application-from-visual-studio"></a>Visual Studio からアプリケーションをテストします。

1. 保存し、ソリューションをビルドします。

2. 選択、 **GettingStartedLib**フォルダー、および選択**スタートアップ プロジェクトとして設定**ショートカット メニューから。

3. **スタートアップ プロジェクト**を選択します**GettingStartedLib**ドロップダウン リストからを選択し、**実行**またはキーを押します**F5**します。

### <a name="test-the-application-from-a-command-prompt"></a>コマンド プロンプトからアプリケーションをテストします。

1. 管理者は、コマンド プロンプトを開きし、Visual Studio のソリューション ディレクトリに移動します。 

2. サービスを開始します。入力*GettingStartedHost\bin\Debug\GettingStartedHost.exe*します。

3. クライアントを起動します。別のコマンド プロンプトを開きし、Visual Studio のソリューション ディレクトリに移動して、入力*GettingStartedClient\bin\Debug\GettingStartedClient.exe*します。

   *GettingStartedHost.exe*次の出力が生成されます。

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   *GettingStartedClient.exe*次の出力が生成されます。

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>次の手順

WCF 入門チュートリアルで、すべてのタスクを完了します。 このチュートリアルでは、次の作業を行う方法を学びました。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> - WCF クライアントを使用するコードを追加します。
> - WCF クライアントをテストします。

手順のいずれかである場合の問題やエラーは場合は、それを修正するトラブルシューティング記事の手順に従います。

> [!div class="nextstepaction"]
> [Get のトラブルシューティングでは、WCF のチュートリアルを開始](troubleshooting-the-getting-started-tutorial.md)

