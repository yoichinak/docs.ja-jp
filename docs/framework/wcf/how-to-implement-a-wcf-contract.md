---
title: 'チュートリアル: Windows 通信基盤サービス コントラクトを実装する'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: debdeeac7064f5bae21622b2d9de84a4d8a0e66f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184065"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>チュートリアル: Windows 通信基盤サービス コントラクトを実装する

このチュートリアルでは、基本的な Wcf (WCF) アプリケーションを作成するために必要な 5 つのタスクの 2 つ目について説明します。 チュートリアルの概要については、「[チュートリアル: Windows コミュニケーションファウンデーション アプリケーションの概要](getting-started-tutorial.md)」を参照してください。

WCF アプリケーションを作成するための次の手順は、前の手順で作成した WCF サービス インターフェイスを実装するコードを追加します。 この手順では、ユーザー定義`CalculatorService``ICalculator`インターフェイスを実装するクラスを作成します。 次のコードの各メソッドは、電卓の操作を呼び出し、コンソールにテキストを書き込んでテストします。

このチュートリアルでは、以下の内容を学習します。
> [!div class="checklist"]
>
> - WCF サービス コントラクトを実装するコードを追加します。
> - ソリューションをビルドします。

## <a name="add-code-to-implement-the-wcf-service-contract"></a>WCF サービス コントラクトを実装するコードを追加します。

**で、Service1.cs**または**Service1.cs****Service1.vb**ファイルを開き、コードを次のコードに置き換えます。

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

## <a name="edit-appconfig"></a>アプリケーション構成の編集

コードに加えた変更を反映するように **、次のコードを取得中に Lib**で**App.config**を編集します。

- Visual C# プロジェクトの場合:
  - 行 14 を次の行に変更`<service name="GettingStartedLib.CalculatorService">`
  - 行 17 を次の行に変更`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 行 22 を次の行に変更します`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Visual Basic プロジェクトの場合は、次の操作を行います。
  - 行 14 を次の行に変更`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - 行 17 を次の行に変更`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 行 22 を次の行に変更します`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>コードのコンパイル

コンパイル エラーがないことを確認するソリューションをビルドします。 Visual Studio を使用している場合は、[**ビルド**] メニューの [**ソリューションのビルド**] を選択します (または**Ctrl**+**Shift**+**B**キーを押します)。

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、以下の内容を学習しました。
> [!div class="checklist"]
>
> - WCF サービス コントラクトを実装するコードを追加します。
> - ソリューションをビルドします。

WCF サービスの実行方法については、次のチュートリアルに進んでください。

> [!div class="nextstepaction"]
> [チュートリアル: 基本的な WCF サービスをホストして実行する](how-to-host-and-run-a-basic-wcf-service.md)
