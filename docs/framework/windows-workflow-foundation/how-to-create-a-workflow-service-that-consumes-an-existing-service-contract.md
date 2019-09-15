---
title: '方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 6d7fa8c9faa84efc84243387cd27aa264f6155eb
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989621"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する
.NET Framework 4.5 では、コントラクト優先ワークフロー開発の形式で web サービスとワークフローの統合が強化されています。 コントラクト優先ワークフローの開発ツールでは、コードのコントラクトを先に設計できます。 その後、ツールボックス内に、コントラクト内の操作用のアクティビティ テンプレートが自動的に生成されます。  
  
> [!NOTE]
> このトピックでは、コントラクト優先ワークフロー サービスを作成する手順について説明します。 コントラクト優先ワークフローサービスの開発の詳細については、「[コントラクトの最初のワークフローサービスの開発](contract-first-workflow-service-development.md)」を参照してください。  
  
### <a name="creating-the-workflow-project"></a>ワークフロー プロジェクトの作成  
  
1. Visual Studio で、 **[ファイル]** 、 **[新しいプロジェクト]** の順番に選択します。 **[テンプレート]** ツリーのノード**C#** の下にある **[wcf]** ノードを選択し、 **[wcf ワークフローサービスアプリケーション]** テンプレートを選択します。  
  
2. 新しいプロジェクト`ContractFirst`に名前を指定し、[ **Ok]** をクリックします。  
  
### <a name="creating-the-service-contract"></a>サービス コントラクトの作成  
  
1. プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の追加**. 左側の **[コード]** ノードを選択し、右側の **[クラス]** テンプレートを選択します。 新しいクラスの名前を`IBookService` をクリック**Ok**です。  
  
2. 表示されるコード ウィンドウの上部で、`System.Servicemodel` に対する Using ステートメントを追加します。  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. サンプルのクラス定義を次のインターフェイス定義に変更します。  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. **Ctrl + Shift + B**キーを押してプロジェクトをビルドします。  
  
### <a name="importing-the-service-contract"></a>サービス コントラクトのインポート  
  
1. **ソリューションエクスプローラー**でプロジェクトを右クリックし、 **[サービスコントラクトのインポート]** を選択します。 **\<現在のプロジェクト >** で、すべてのサブノードを開き、**ibookservice** を選択します。 **[OK]** をクリックします。  
  
2. ダイアログが表示され、操作が正常に完了したことと、プロジェクトをビルドすると、生成されたアクティビティがツールボックスに表示されることが示されます。 **[OK]** をクリックします。  
  
3. **Ctrl + Shift + B**キーを押してプロジェクトをビルドし、インポートされたアクティビティがツールボックスに表示されるようにします。  
  
4. **ソリューションエクスプローラー**で、Service1 .xamlx を開きます。 ワークフロー サービスがデザイナーに表示されます。  
  
5. **Sequence**アクティビティを選択します。 プロパティウィンドウで、. **.**  をクリックします。 **ImplementedContract**プロパティのボタン。 **[型コレクションエディター]** ウィンドウが表示されたら、 **[種類]** ドロップダウンをクリックし、 **[種類の参照]** を選択します。 キー. **.Net 型の参照と選択** ダイアログボックスの   **\<現在のプロジェクト >** で、すべてのサブノードを開き、**ibookservice** を選択します。 **[OK]** をクリックします。 **[型コレクションエディター]** ダイアログボックスで、[ **OK]** をクリックします。  
  
6. **Receiverequest アクティビティ**アクティビティと**sendresponse**アクティビティを選択して削除します。  
  
7. [ツールボックス] から、 **Buy_ReceiveAndSendReply**アクティビティと**Checkout_Receive**アクティビティを**シーケンシャルサービス**アクティビティにドラッグします。
