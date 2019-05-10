---
title: 'チュートリアル: データの操作 (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 0dd70eb5d3b3ad56a8597ce0658a296a03d5f4a7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64618048"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>チュートリアル: データの操作 (Visual Basic)
このチュートリアルでは、データベースに対してデータの追加、変更、および削除を行う、基本の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。 顧客の追加、顧客名の変更、および注文の削除を行うため、サンプルの Northwind データベースのコピーを使用します。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 このチュートリアルは、Visual Basic 開発設定を使用して記述されています。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルの前提条件は次のとおりです。  
  
- このチュートリアルでは、専用フォルダー ("c:\linqtest2") を使用してファイルを保持します。 チュートリアルを開始する前に、このフォルダーを作成してください。  
  
- Northwind サンプル データベース。  
  
     開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。 手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)します。 データベースをダウンロードしたら、northwnd.mdf ファイルを c:\linqtest2 フォルダーにコピーします。  
  
- Northwind データベースから生成された Visual Basic コード ファイル。  
  
     このファイルを生成するには、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]または SQLMetal ツールを使用します。 このチュートリアルは、SQLMetal ツールを使用して次のコマンド ラインで作成されています。  
  
     **sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**  
  
     詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="overview"></a>概要  
 このチュートリアルは、主に次の 6 つのタスクで構成されています。  
  
- 作成、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio でソリューション。  
  
- プロジェクトにデータベース コード ファイルを追加します。  
  
- 新しい顧客オブジェクトを作成します。  
  
- 顧客の連絡先名を変更します。  
  
- 注文を削除します。  
  
- これらの変更を Northwind データベースに送信します。  
  
## <a name="creating-a-linq-to-sql-solution"></a>LINQ to SQL ソリューションを作成する  
 この最初のタスクでは、ビルドおよび実行するために必要な参照を含む Visual Studio ソリューションを作成、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]プロジェクト。  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>LINQ to SQL ソリューションを作成するには  
  
1. Visual Studio で **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。  
  
2. **プロジェクトの種類**ペインで、**新しいプロジェクト**ダイアログ ボックスで、をクリックして**Visual Basic**します。  
  
3. **[テンプレート]** ペインの **[コンソール アプリケーション]** をクリックします。  
  
4. **名前**ボックスに「 **LinqDataManipulationApp**します。  
  
5. **[OK]** をクリックします。  
  
## <a name="adding-linq-references-and-directives"></a>LINQ の参照とディレクティブを追加する  
 このチュートリアルで使用するアセンブリは、既定ではプロジェクトにインストールされていない場合があります。 場合`System.Data.Linq`がプロジェクトの参照として表示されない (をクリックして**すべてのファイル**で**ソリューション エクスプ ローラー**を展開し、**参照**ノード) で説明したように、それを追加次の手順。  
  
#### <a name="to-add-systemdatalinq"></a>System.Data.Linq を追加するには  
  
1. **ソリューション エクスプ ローラー**を右クリックして**参照**、 をクリックし、**参照の追加**します。  
  
2. **参照の追加**ダイアログ ボックスで、をクリックして **.NET**、System.Data.Linq アセンブリをクリックし、順にクリックして、 **[ok]** します。  
  
     アセンブリがプロジェクトに追加されます。  
  
3. コード エディターで上記の次のディレクティブを追加**Module1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>プロジェクトに Northwind コード ファイルを追加する  
 これらの手順では、SQLMetal ツールを使用して Northwind サンプル データベースからコード ファイルを生成していることが前提です。 詳細については、このチュートリアルの「前提条件」を参照してください。  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>プロジェクトに Northwind コード ファイルを追加するには  
  
1. **[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。  
  
2. **既存項目の追加**ダイアログ ボックスは c:\linqtest2\northwind.vb に移動し、をクリックし、**追加**します。  
  
     プロジェクトに northwind.vb ファイルが追加されます。  
  
## <a name="setting-up-the-database-connection"></a>データベース接続の設定  
 最初に、データベースへの接続をテストします。 データベースの名前 Northwnd に i の文字が欠けていることに注意してください。 次の手順でエラーが生成された後で、northwind.vb ファイルを調べて、Northwind 部分クラスのスペルを確認します。  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>データベース接続を設定してテストするには  
  
1. `Sub Main` に次のコードを入力するか、貼り付けます。  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. この時点でアプリケーションをテストするには、F5 キーを押します。  
  
     A**コンソール**ウィンドウが開きます。  
  
     Enter キーを押してアプリケーションを閉じて、**コンソール**ウィンドウで、またはをクリックして**デバッグの停止** Visual Studio で**デバッグ**メニュー。  
  
## <a name="creating-a-new-entity"></a>新しいエンティティの作成  
 新しいエンティティを作成する手順は簡単です。 `Customer` キーワードを使用してオブジェクト (`New` など) を作成できます。  
  
 以降のセクションでは、ローカル キャッシュのみに変更を加えます。 このチュートリアルの終盤で <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すまで、変更内容はデータベースに送信されません。  
  
#### <a name="to-add-a-new-customer-entity-object"></a>新しい Customer エンティティ オブジェクトを追加するには  
  
1. 次のコードを `Customer` 内の `Console.ReadLine` の前に追加することで、新しい `Sub Main` を作成します。  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. F5 キーを押してソリューションをデバッグします。  
  
     結果は、以下のようにコンソール ウィンドウに表示されます。  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     新しい行は結果に表示されません。 新しいデータは、まだデータベースに送信されていません。  
  
3. Enter キーを押して、**コンソール**デバッグを停止するウィンドウ。  
  
## <a name="updating-an-entity"></a>エンティティの更新  
 以降の手順では、`Customer` オブジェクトを取得し、そのプロパティの 1 つを変更します。  
  
#### <a name="to-change-the-name-of-a-customer"></a>顧客の名前を変更するには  
  
- `Console.ReadLine()` の前に次のコードを追加します。  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>エンティティの削除  
 同じ顧客オブジェクトを使用して、最初の注文を削除できます。  
  
 行間のリレーションシップを切断し、データベースから行を削除する方法を次のコードに示します。  
  
#### <a name="to-delete-a-row"></a>行を削除するには  
  
- `Console.ReadLine()` の直前に次のコードを追加します。  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>変更内容のデータベースへの送信  
 最後の手順は、オブジェクトの作成、更新、および削除を実際にデータベースに送信するために必要です。 この手順を行わないと、変更はローカルのみに留まり、クエリの結果には反映されません。  
  
#### <a name="to-submit-changes-to-the-database"></a>データベースに変更内容を送信するには  
  
1. `Console.ReadLine` の直前に次のコードを挿入します。  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. 変更内容の送信前と送信後の変化を示すために、次のコードを (`SubmitChanges` の後に) 挿入します。  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. F5 キーを押してソリューションをデバッグします。  
  
     次のようにコンソール ウィンドウが表示されます。  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. Enter キーを押して、**コンソール**デバッグを停止するウィンドウ。  
  
> [!NOTE]
>  変更内容を送信して新しい顧客を追加した後で、このソリューションを再度実行することはできません。同じ顧客を再度追加できないためです。 ソリューションを再度実行するには、追加する顧客 ID の値を変更します。  
  
## <a name="see-also"></a>関連項目

- [チュートリアルによる学習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
