---
title: 'チュートリアル: ストアド プロシージャのみを使用する (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: f980402c976db9ee327a7b726e36a0a4d9d6d73f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792096"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>チュートリアル: ストアド プロシージャのみを使用する (C#)

このチュートリアルでは、ストアド プロシージャを実行することでのみデータにアクセスする、基本的な [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。 この方法は、データ ストアへのアクセス方法を制限する目的で、データベース管理者によってよく使用されます。

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションでストアド プロシージャを使用して、既定の動作をオーバーライドすることもできます。これは、`Create`、`Update`、および `Delete` の各プロセスで特に役立ちます。 詳細については、「[挿入、更新、および削除の操作をカスタマイズ](customizing-insert-update-and-delete-operations.md)する」を参照してください。

このチュートリアルでは、Northwind サンプルデータベースのストアドプロシージャにマップされている2つのメソッドを使用します。CustOrdersDetail と CustOrderHist。 このマップは、SqlMetal コマンド ライン ツールを実行して C# ファイルを生成したときに作成されます。 詳細については、このチュートリアルの「前提条件」を参照してください。

このチュートリアルは、オブジェクトリレーショナルデザイナーに依存しません。 Visual Studio を使用する開発者は、O/R デザイナーを使用してストアドプロシージャ機能を実装することもできます。 「 [Visual Studio の LINQ to SQL ツール」を](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)参照してください。

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

このチュートリアルは、Visual C# 開発設定を使用して記述されています。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルの前提条件は次のとおりです。

- このチュートリアルでは、専用フォルダー ("c:\linqtest7") を使用してファイルを保持します。 チュートリアルを開始する前に、このフォルダーを作成してください。

- Northwind サンプル データベース。

     開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。 手順については、「[サンプルデータベースのダウンロード](downloading-sample-databases.md)」を参照してください。 データベースをダウンロードしたら、northwnd.mdf ファイルを c:\linqtest7 フォルダーにコピーします。

- Northwind データベースから生成された C# コード ファイル。

     このチュートリアルは、SqlMetal ツールを使用して次のコマンド ラインで作成されています。

     **sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**

     詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。

## <a name="overview"></a>概要

このチュートリアルは、主に次の 6 つのタスクで構成されています。

- Visual Studio でソリューションを設定します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]

- プロジェクトに System.Data.Linq アセンブリを追加します。

- プロジェクトにデータベース コード ファイルを追加します。

- データベースへの接続を作成します。

- ユーザー インターフェイスを設定します。

- アプリケーションを実行およびテストします。

## <a name="creating-a-linq-to-sql-solution"></a>LINQ to SQL ソリューションを作成する

この最初のタスクでは、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]プロジェクトをビルドして実行するために必要な参照を含む Visual Studio ソリューションを作成します。

### <a name="to-create-a-linq-to-sql-solution"></a>LINQ to SQL ソリューションを作成するには

1. Visual Studio の **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2. **[新しいプロジェクト]** ダイアログボックスの **[プロジェクトの種類]** ペインで、 **[ビジュアルC# ]** をクリックします。

3. **[テンプレート]** ペインの **[Windows フォーム アプリケーション]** をクリックします。

4. **[名前]** ボックスに「 **Sprocon氏アプリ**」と入力します。

5. **[場所]** ボックスで、プロジェクトファイルを保存する場所を確認します。

6. **[OK]** をクリックします。

     Windows フォーム デザイナーが開きます。

## <a name="adding-the-linq-to-sql-assembly-reference"></a>LINQ to SQL アセンブリ参照を追加する

標準の Windows フォーム アプリケーション テンプレートには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アセンブリは含まれていません。 次の手順に従って、アセンブリを自分で追加する必要があります。

### <a name="to-add-systemdatalinqdll"></a>System.Data.Linq.dll を追加するには

1. **ソリューションエクスプローラー**で、 **[参照]** を右クリックし、 **[参照の追加]** をクリックします。

2. **[参照の追加]** ダイアログボックスで **[.net]** をクリックし、system.string アセンブリをクリックして、 **[OK]** をクリックします。

     アセンブリがプロジェクトに追加されます。

## <a name="adding-the-northwind-code-file-to-the-project"></a>プロジェクトに Northwind コード ファイルを追加する

この手順では、事前に SqlMetal ツールを使用して、Northwind サンプル データベースからコード ファイルを生成していることが前提となります。 詳細については、このチュートリアルの「前提条件」を参照してください。

### <a name="to-add-the-northwind-code-file-to-the-project"></a>プロジェクトに Northwind コード ファイルを追加するには

1. **[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。

2. **[既存項目の追加]** ダイアログボックスで、c:\linqtest7\ northwind.cs に移動し、 **[追加]** をクリックします。

     northwind.cs ファイルがプロジェクトに追加されます。

## <a name="creating-a-database-connection"></a>データベース接続を作成する

この手順では、Northwind サンプル データベースへの接続を定義します。 このチュートリアルでは、パスとして "c:\linqtest7\northwnd.mdf" を使用します。

### <a name="to-create-the-database-connection"></a>データベース接続を作成するには

1. **ソリューションエクスプローラー**で、 **[Form1.cs]** を右クリックし、 **[コードの表示]** をクリックします。

2. `Form1` クラスに次のコードを入力します。

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a>ユーザー インターフェイスを設定する

この手順では、ユーザーがストアド プロシージャを実行してデータベース内のデータにアクセスできるように、インターフェイスを設定します。 このチュートリアルで作成するアプリケーションでは、ユーザーがデータベース内のデータにアクセスできる手段は、アプリケーションに埋め込まれたストアド プロシージャを使用することだけです。

### <a name="to-set-up-the-user-interface"></a>ユーザー インターフェイスを設定するには

1. Windows フォームデザイナーに戻ります (**Form1 [Design]** )。

2. **[表示]** メニューの **[ツールボックス]** をクリックします。

     ツールボックスが表示されます。

    > [!NOTE]
    > **[自動的に隠す]** をクリックして、このセクションの残りの手順を実行しながら、ツールボックスを開いたままにします。

3. ツールボックスから**Form1**に2つのボタン、2つのテキストボックス、2つのラベルをドラッグします。

     図のようにコントロールを配置します。 **[Form1]** を展開して、コントロールが簡単に見えるようにします。

4. **[Label1]** を右クリックし、 **[プロパティ]** をクリックします。

5. **[Text]** プロパティを 「Label1 **」から「Enter OrderID:」** に変更します。

6. **Label2**の場合と同じように、 **Text**プロパティを**label2**から**CustomerID:** に変更します。

7. 同様に、 **button1**の**Text**プロパティを**Order Details**に変更します。

8. **Button2**の**Text**プロパティを「 **Order History**」に変更します。

     すべてのテキストが表示されるように、ボタン コントロールの幅を広げます。

### <a name="to-handle-button-clicks"></a>ボタン クリックを処理するには

1. **Form1**の **[Order Details]** をダブルクリックして、コードエディターで button1 イベントハンドラーを開きます。

2. `button1` のハンドラーに次のコードを入力します。

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. ここで、 **Form1**の**button2**をダブルクリックし`button2`て、ハンドラーを開きます。

4. `button2` のハンドラーに次のコードを入力します。

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a>アプリケーションのテスト

次に、アプリケーションをテストします。 データ ストアに対する操作は、2 つのストアド プロシージャで実行できる処理に制限されることに注意してください。 つまり、入力した orderID に含まれている製品を返す処理と、入力した CustomerID の注文製品の履歴を返す処理のみを実行できます。

### <a name="to-test-the-application"></a>アプリケーションをテストするには

1. F5 キーを押してデバッグを開始します。

     Form1 が表示されます。

2. **[OrderID の入力]** ボックスに`10249`「」と入力し、 **[Order Details]** をクリックします。

     注文 10249 に含まれている製品がメッセージ ボックスに表示されます。

     [ **OK]** をクリックして、メッセージボックスを閉じます。

3. **[CustomerID の入力]** ボックスに`ALFKI`「」と入力し、 **[注文履歴]** をクリックします。

     顧客 ALFKI の注文履歴がメッセージ ボックスに表示されます。

     [ **OK]** をクリックして、メッセージボックスを閉じます。

4. **[OrderID の入力]** ボックスに`123`「」と入力し、 **[Order Details]** をクリックします。

     "No results" というメッセージ ボックスが表示されます。

     [ **OK]** をクリックして、メッセージボックスを閉じます。

5. **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。

     デバッグ セッションが終了します。

6. 実験が終了したら、 **[ファイル]** メニューの **[プロジェクトを閉じる]** をクリックし、メッセージが表示されたらプロジェクトを保存します。

## <a name="next-steps"></a>次の手順

いくつかの変更を加えることによって、このプロジェクトを強化できます。 たとえば、使用できるストアド プロシージャの一覧をリスト ボックスに表示し、実行するプロシージャをユーザーに選択させることができます。 レポートの出力をテキスト ファイルに送ることもできます。

## <a name="see-also"></a>関連項目

- [チュートリアルによる学習](learning-by-walkthroughs.md)
- [ストアド プロシージャ](stored-procedures.md)
