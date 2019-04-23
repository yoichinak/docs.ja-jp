---
title: '方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: c2ca9c349718c3939d74d052ff0ed448879cd045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344716"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、コントラクト優先ワークフローの開発という形で、Web サービスとワークフローの統合が向上しています。 コントラクト優先ワークフローの開発ツールでは、コードのコントラクトを先に設計できます。 その後、ツールボックス内に、コントラクト内の操作用のアクティビティ テンプレートが自動的に生成されます。  
  
> [!NOTE]
>  このトピックでは、コントラクト優先ワークフロー サービスを作成する手順について説明します。 コントラクト優先ワークフロー サービスの開発の詳細については、次を参照してください。[コントラクト優先ワークフロー サービスの開発](contract-first-workflow-service-development.md)します。  
  
### <a name="creating-the-workflow-project"></a>ワークフロー プロジェクトの作成  
  
1. Visual Studio で、次のように選択します。**ファイル**、**新しいプロジェクト**します。 選択、 **WCF**ノードの下、 **C#** 内のノード、**テンプレート**ツリー、および選択、 **WCF ワークフロー サービス アプリケーション**テンプレート。  
  
2. 新しいプロジェクトの名前`ContractFirst`クリック**Ok**します。  
  
### <a name="creating-the-service-contract"></a>サービス コントラクトの作成  
  
1. プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の追加**. 選択、**コード**、左側のノードと**クラス**右側のテンプレート。 新しいクラスの名前を`IBookService` をクリック**Ok**です。  
  
2. 表示されるコード ウィンドウの上部で、`System.Servicemodel` に対する Using ステートメントを追加します。  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3. サンプルのクラス定義を次のインターフェイス定義に変更します。  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. キーを押してプロジェクトをビルド**Ctrl + Shift + B**します。  
  
### <a name="importing-the-service-contract"></a>サービス コントラクトのインポート  
  
1. プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**サービス コントラクトのインポート**します。 **\<現在のプロジェクト >** すべてのサブノードを開き、選択**IBookService**します。 **[OK]** をクリックします。  
  
2. ダイアログが表示され、操作が正常に完了したことと、プロジェクトをビルドすると、生成されたアクティビティがツールボックスに表示されることが示されます。 **[OK]** をクリックします。  
  
3. キーを押してプロジェクトをビルド**Ctrl + Shift + B**、インポートしたアクティビティがツールボックスに表示されるようにします。  
  
4. **ソリューション エクスプ ローラー**Service1.xamlx を開きます。 ワークフロー サービスがデザイナーに表示されます。  
  
5. 選択、**シーケンス**アクティビティ。 [プロパティ] ウィンドウ、 **.** ボタン、 **ImplementedContract**プロパティ。 **型コレクション エディター**ウィンドウが表示されたら、クリックして、**型**ドロップダウンを選択し、 **型の参照.** エントリ。 **を参照して .NET 型を選択**ダイアログで、 **\<現在のプロジェクト >** すべてのサブノードを開き、選択**IBookService**します。 **[OK]** をクリックします。 **型コレクション エディター**ダイアログ ボックスで、をクリックして**OK**します。  
  
6. 選択し、削除、 **ReceiveRequest**と**SendResponse**アクティビティ。  
  
7. ツールボックスからドラッグして、 **Buy_ReceiveAndSendReply**と**Checkout_Receive**にアクティビティ、**シーケンシャル サービス**アクティビティ。
