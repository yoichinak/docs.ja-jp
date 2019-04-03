---
title: 'チュートリアル: Windows Communication Foundation サービス コントラクトを実装します。'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fa8c5457c636d7f37215f0d4b4fdbb1c96c9481e
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463619"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>チュートリアル: Windows Communication Foundation サービス コントラクトを実装します。

このチュートリアルでは、2 番目の基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な 5 つのタスクについて説明します。 チュートリアルの概要については、[チュートリアル。Windows Communication Foundation アプリケーションの概要](getting-started-tutorial.md)を参照してください。

WCF アプリケーションを作成する場合は、次の手順では、前の手順で作成した WCF サービスのインターフェイスを実装するコードを追加します。 この手順でという名前のクラスを作成する`CalculatorService`ユーザー定義を実装する`ICalculator`インターフェイス。 次のコード内の各メソッドでは、電卓操作を呼び出すし、テスト コンソールにテキストを書き込みます。 

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> - WCF サービス コントラクトを実装するコードを追加します。
> - ソリューションをビルドします。

## <a name="add-code-to-implement-the-wcf-service-contract"></a>WCF サービス コントラクトを実装するコードを追加します。

**GettingStartedLib**、オープン、 **Service1.cs**または**Service1.vb**ファイルし、そのコードを次のコードに置き換えます。

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

## <a name="edit-appconfig"></a>App.config を編集します。

編集**App.config**で**GettingStartedLib**コードに加えた変更を反映します。
- ビジュアルのC#プロジェクト。
  - 14 行を変更します。 `<service name="GettingStartedLib.CalculatorService">`
  - 行 17 を変更します。 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 変更するには、22 行目 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Visual Basic プロジェクトの場合は、次の操作を行います。
  - 14 行を変更します。 `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - 行 17 を変更します。 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 変更するには、22 行目 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>コードのコンパイル

コンパイル エラーがないことを確認するソリューションをビルドします。 Visual Studio を使用している場合、**ビルド**メニューの **ソリューションのビルド**(またはキーを押します**Ctrl**+**Shift** + **B**)。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> - WCF サービス コントラクトを実装するコードを追加します。
> - ソリューションをビルドします。

WCF サービスを実行する方法については、次のチュートリアルに進んでください。

> [!div class="nextstepaction"]
> [チュートリアル: ホストおよび基本的な WCF サービスの実行](how-to-host-and-run-a-basic-wcf-service.md)
