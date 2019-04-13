---
title: 'チュートリアル: Windows Communication Foundation サービス コントラクトを定義します。'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228394"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>チュートリアル: Windows Communication Foundation サービス コントラクトを定義します。

このチュートリアルでは、最初の基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な 5 つのタスクについて説明します。 チュートリアルの概要については、次を参照してください。[チュートリアル。Windows Communication Foundation アプリケーションの概要](getting-started-tutorial.md)します。

WCF サービスを作成するときに、最初のタスクは、サービス コントラクトを定義します。 サービス コントラクトは、サービスがサポートする操作を指定します。 操作は Web サービス メソッドと見なすことができます。 ビジュアルを定義してサービス コントラクトを作成するC#または Visual Basic (VB) インターフェイス。 インターフェイスには、次の特徴があります。

- インターフェイスの各メソッドは、特定のサービス操作に対応しています。 
- インターフェイスごとに適用する必要があります、<xref:System.ServiceModel.ServiceContractAttribute>属性。
- 各操作またはメソッドに適用する必要があります、<xref:System.ServiceModel.OperationContractAttribute>属性。 

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> - 作成、 **WCF サービス ライブラリ**プロジェクト。
> - サービス コントラクト インターフェイスを定義します。

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>WCF サービス ライブラリ プロジェクトを作成し、サービス コントラクト インターフェイスの定義

1. Visual Studio を管理者として開きます。 これを行うで Visual Studio のプログラムを選択します。、**開始**] メニューの [クリックして**詳細** > **管理者として実行**ショートカット メニューから。

2. 作成、 **WCF サービス ライブラリ**プロジェクト。

   1. **[ファイル]** メニューで、**[新規作成]**、 > **[プロジェクト]** の順に作成します。

   2. **新しいプロジェクト**] ダイアログの左側にある [展開**Visual c#** または**Visual Basic**、クリックして、 **WCF**カテゴリ。 Visual Studio は、ウィンドウの中央のセクションで、プロジェクト テンプレートの一覧を表示します。 選択**WCF サービス ライブラリ**します。

      > [!NOTE]
      > 表示されない場合、 **WCF**プロジェクト テンプレートのカテゴリをインストールする必要があります、 **Windows Communication Foundation** Visual Studio のコンポーネント。 **新しいプロジェクト**ダイアログ ボックスで、 **Visual Studio インストーラーを開く**左側にあるリンクです。 選択、**個々 のコンポーネント**] タブの [、し、検索して選択します**Windows Communication Foundation**下、**開発アクティビティ**カテゴリ。 選択**変更**コンポーネントのインストールを開始します。

   3. ウィンドウの下部のセクションで次のように入力します。 *GettingStartedLib*の、**名前**と*GettingStarted*の、**ソリューション名**します。 

   4. **[OK]** を選択します。

      Visual Studio では、プロジェクトを 3 つのファイルが作成されます。*IService1.cs* (または*IService1.vb* Visual Basic プロジェクトの)、 *Service1.cs* (または*Service1.vb* Visual Basic プロジェクトの)、および*App.config*します。Visual Studio では、次のように、これらのファイルを定義します。 
      - *IService1*ファイルには、サービス コントラクトの既定の定義が含まれています。 
      - *Service1*ファイルには、サービス コントラクトの既定の実装が含まれています。 
      - *App.config*ファイルには、Visual Studio WCF サービス ホスト ツールを使用して既定のサービスを読み込むために必要な構成情報が含まれています。 WCF サービス ホスト ツールの詳細については、次を参照してください。 [WCF サービス ホスト (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)します。

      > [!NOTE]
      > Visual Basic 開発者設定が環境で Visual Studio をインストールした場合、ソリューションを非表示に可能性があります。 大文字と小文字の場合は、選択**オプション**から、**ツール**メニューを選択し、**プロジェクトおよびソリューション** > **全般**で**オプション**ウィンドウ。 選択**常にソリューションを表示する**します。 また、いることを確認**作成時に新しいプロジェクトを保存**が選択されています。

3. **ソリューション エクスプ ローラー**、オープン、 **IService1.cs**または**IService1.vb**ファイルを開き、そのコードを次のコードに置き換えます。

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
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
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     このコントラクトは、オンライン電卓を定義します。 通知、`ICalculator`インターフェイスが付いて、<xref:System.ServiceModel.ServiceContractAttribute>属性 (として簡略化された`ServiceContract`)。 この属性は、コントラクト名を明確に区別する名前空間を定義します。 コードでは、各電卓操作をマークする、<xref:System.ServiceModel.OperationContractAttribute>属性 (として簡略化された`OperationContract`)。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> - WCF サービス ライブラリ プロジェクトを作成します。
> - サービス コントラクト インターフェイスを定義します。

WCF サービス コントラクトを実装する方法については、次のチュートリアルに進んでください。

> [!div class="nextstepaction"]
> [チュートリアル: WCF サービス コントラクトを実装します。](how-to-implement-a-wcf-contract.md)
