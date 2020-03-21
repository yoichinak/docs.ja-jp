---
title: 'チュートリアル: Windows 通信基盤サービス コントラクトの定義'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184090"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>チュートリアル: Windows 通信基盤サービス コントラクトの定義

このチュートリアルでは、基本的な Wcf (WCF) アプリケーションを作成するために必要な 5 つのタスクの最初の作業について説明します。 チュートリアルの概要については、「[チュートリアル: Windows コミュニケーションファウンデーション アプリケーションの概要](getting-started-tutorial.md)」を参照してください。

WCF サービスを作成する場合、最初のタスクはサービス コントラクトを定義することです。 サービス コントラクトでは、サービスがサポートする操作を指定します。 操作は Web サービス メソッドと見なすことができます。 サービス コントラクトを作成するには、C# または Visual Basic インターフェイスを定義します。 インターフェイスには、次の特性があります。

- インターフェイスの各メソッドは、特定のサービス操作に対応しています。
- 各インターフェイスに対して、属性を<xref:System.ServiceModel.ServiceContractAttribute>適用する必要があります。
- 各操作/メソッドに対して、属性を<xref:System.ServiceModel.OperationContractAttribute>適用する必要があります。

このチュートリアルでは、以下の内容を学習します。
> [!div class="checklist"]
>
> - WCF**サービス ライブラリ**プロジェクトを作成します。
> - サービス コントラクト インターフェイスを定義します。

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>WCF サービス ライブラリ プロジェクトを作成し、サービス コントラクト インターフェイスを定義します。

1. Visual Studio を管理者として開きます。 これを行うには、[**スタート]** メニューで Visual Studio プログラムを選択し、ショートカット メニューから **[管理者としてその他** > の**実行**] を選択します。

2. WCF**サービス ライブラリ**プロジェクトを作成します。

   1. **[ファイル]** メニューから、**[新規]** > **[プロジェクト]** の順に選択します。

   2. [**新しいプロジェクト**] ダイアログ ボックスの左側で **、[Visual C#]** または **[Visual Basic]** を展開し **、[WCF]** カテゴリを選択します。 プロジェクト テンプレートの一覧がウィンドウの中央セクションに表示されます。 [WCF**サービス ライブラリ**] を選択します。

      > [!NOTE]
      > **WCF**プロジェクト テンプレート カテゴリが表示されない場合は、Visual Studio の**Windows コミュニケーション基礎**コンポーネントをインストールする必要があります。 [**新しいプロジェクト**] ダイアログ ボックスで、左側にある **[Visual Studio インストーラーを開く**] リンクを選択します。 [**個々のコンポーネント**] タブを選択し、[**開発活動**] カテゴリの下にある **[Windows コミュニケーション 基盤**] を検索して選択します。 [**変更]** を選択して、コンポーネントのインストールを開始します。

   3. ウィンドウの下部に、「**名前***」に「はじめに開始」* と入力し、**ソリューション名***に「はじめに*」と入力します。

   4. **[OK]** を選択します。

      プロジェクトは *、IService1.cs* (または Visual Basic プロジェクトの*場合は IService1.vb)、Service1.cs* (または Visual Basic プロジェクトの場合は*Service1.vb)、**および App.config*の 3 つのファイルを含むプロジェクトを作成します。 *Service1.cs*これらのファイルは、次のように定義されます。
      - *IService1*ファイルには、サービス コントラクトの既定の定義が含まれています。
      - *Service1*ファイルには、サービス コントラクトの既定の実装が含まれています。
      - *App.config*ファイルには、Visual Studio WCF サービス ホスト ツールを使用して既定のサービスを読み込むために必要な構成情報が含まれています。 WCF サービス ホスト ツールの詳細については[、「WCF サービス ホスト (WcfSvcHost.exe)」を参照してください](wcf-service-host-wcfsvchost-exe.md)。

      > [!NOTE]
      > Visual Basic の開発者環境設定を使用して Visual Studio をインストールした場合、ソリューションが非表示になっている可能性があります。 この場合は、[**ツール**] メニューの **[オプション]** を選択し、[**オプション]** **ウィンドウで**[**プロジェクトとソリューション** > 全般] を選択します。 [**常にソリューションを表示する] を選択**します。 また、[**作成時に新しいプロジェクトを保存]** が選択されていることを確認します。

3. **ソリューション エクスプローラー**で **、IService1.cs**または**IService1.vb**ファイルを開き、コードを次のコードに置き換えます。

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

     このコントラクトは、オンライン電卓を定義します。 インターフェイスに`ICalculator`<xref:System.ServiceModel.ServiceContractAttribute>属性が付いていることに注意`ServiceContract`してください ( として簡略化されます)。 この属性は、コントラクト名を明確にする名前空間を定義します。 このコードは、各電卓の<xref:System.ServiceModel.OperationContractAttribute>操作を属性でマーク`OperationContract`します (として簡略化)。

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、以下の内容を学習しました。
> [!div class="checklist"]
>
> - WCF サービス ライブラリ プロジェクトを作成します。
> - サービス コントラクト インターフェイスを定義します。

WCF サービス コントラクトを実装する方法については、次のチュートリアルに進みます。

> [!div class="nextstepaction"]
> [チュートリアル: WCF サービス コントラクトを実装する](how-to-implement-a-wcf-contract.md)
