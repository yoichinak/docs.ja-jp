---
title: チュートリアルによる学習
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: 4beb9944a13fd2f76d7305b4d84230fcc33483be
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781317"
---
# <a name="learning-by-walkthroughs"></a>チュートリアルによる学習
ドキュメント[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]には、いくつかのチュートリアルが用意されています。 このトピックでは、チュートリアルに関する全般的な話題 (トラブルシューティングを含む) を取り上げます。また、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] について学ぶための、いくつかの入門レベルのチュートリアルへのリンクを示します。  
  
> [!NOTE]
> この「入門のためのチュートリアル」のセクションのチュートリアルでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術をサポートする基本的なコードを紹介します。 実際には、オブジェクトリレーショナルデザイナープロジェクトと Windows フォームプロジェクトを使用して[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 、アプリケーションを実装します。 O/R デザイナーのドキュメントには、この目的のための例とチュートリアルが記載されています。  
  
## <a name="getting-started-walkthroughs"></a>入門のためのチュートリアル  
 このセクションではいくつかのチュートリアルを示します。 これらのチュートリアルは、Northwind サンプル データベースを基にしており、複雑さを抑えて、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の機能を少しずつ導入していきます。  
  
 一般的な流れは次のとおりです。  
  
|目標|Visual Basic|C#|  
|---------------|------------------|---------|  
|エンティティ クラスを作成し、簡単なクエリを実行します。|[チュートリアル: 単純なオブジェクトモデルとクエリ (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md)|[チュートリアル: 単純なオブジェクトモデルとクエリC#()](walkthrough-simple-object-model-and-query-csharp.md)|  
|2 番目のクラスを追加し、より複雑なクエリを実行します<br /><br /> (前のチュートリアルを完了している必要があります)。|[チュートリアル: リレーションシップ間でのクエリの実行 (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md)|[チュートリアル: リレーションシップ間のクエリC#()](walkthrough-querying-across-relationships-csharp.md)|  
|データベースの項目を追加、変更、および削除します。|[チュートリアル: データの操作 (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)|[チュートリアル: データの操作C#()](walkthrough-manipulating-data-csharp.md)|  
|ストアド プロシージャを使用します。|[チュートリアル: ストアドプロシージャのみを使用する (Visual Basic)](walkthrough-using-only-stored-procedures-visual-basic.md)|[チュートリアル: ストアドプロシージャのみを使用C#する ()](walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>全般  
 以下の情報は、これらのチュートリアル全体に該当します。  
  
- 環境:各[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]チュートリアルでは、Visual Studio を統合開発環境 (IDE) として使用します。  
  
- SQL エンジン:これらのチュートリアルは、SQL Server Express を使用して実装するように記述されています。 SQL Server Express を持っていない場合は、無料でダウンロードできます。 詳細については、「[サンプルデータベースのダウンロード](downloading-sample-databases.md)」を参照してください。  
  
    > [!NOTE]
    > [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のチュートリアルでは、ファイル名を接続文字列として使用します。 ファイル名を指定するだけで済むのは、SQL Server Express ユーザーのために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に備わっている機能です。 セキュリティ問題には常に注意してください。 詳細については、「 [LINQ to SQL のセキュリティ](security-in-linq-to-sql.md)」を参照してください。  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]チュートリアルには、通常、Northwind サンプルデータベースが必要です。 詳細については、「[サンプルデータベースのダウンロード](downloading-sample-databases.md)」を参照してください。  
  
- チュートリアルに表示されるダイアログボックスとメニューコマンドは、アクティブな設定または Visual Studio のエディションによっては、ヘルプに記載されているものと異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
- 多階層のシナリオに関連するチュートリアルでは、開発用コンピューターとは別のコンピューターにサーバーが配置されていることと、そのサーバーにアクセスするための適切なアクセス許可が必要です。  
  
- 通常、Northwind サンプル データベースの Orders テーブルを表すクラスの名前は `[Order]` です。 が Visual Basic のキーワードで`Order`あるため、エスケープが必要です。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 これらのチュートリアルで使用するデータベースにアクセスするための十分なアクセス許可がない場合、ランタイム エラーが発生することがあります。 特に一般的な問題を解決するためのヒントについては、以下の手順を参照してください。  
  
### <a name="log-on-issues"></a>ログオンの問題  
 アプリケーションが試みているデータベース アクセスの方法が、データベースが受け付けないログオン方法である可能性があります。  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>データベース ログオンを確認または変更するには  
  
1. Windows の **スタート** ボタンをクリックし、**すべてのプログラム**、 **Microsoft SQL Server 2005**、**構成ツール** の順にポイントし、**SQL Server 構成マネージャー** をクリックします。  
  
2. **SQL Server 構成マネージャー**の左ペインで、 **[SQL Server 2005 サービス]** をクリックします。  
  
3. 右ペインで、 **[SQL Server (SQLEXPRESS)]** を右クリックし、 **[プロパティ]** をクリックします。  
  
4. **[ログオン]** タブをクリックし、サーバーへのログオンを試行する方法を確認します。  
  
     ほとんどの場合、**ローカルシステム**は機能します。  
  
     変更を行った場合は、 **[再起動]** をクリックしてサービスを再起動します。  
  
### <a name="protocols"></a>プロトコル  
 場合によっては、アプリケーションがデータベースにアクセスするためのプロトコルが正しく設定されていないこともあります。 たとえば、の[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]チュートリアルに必要な**名前付きパイプ**プロトコルは、既定では有効になっていません。  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>名前付きパイプ プロトコルを有効にするには  
  
1. **SQL Server 構成マネージャー**の左側のウィンドウで、 **[SQL Server 2005 ネットワーク構成]** を展開し、 **[SQLEXPRESS のプロトコル]** をクリックします。  
  
2. 右側のウィンドウで、**名前付きパイプ**プロトコルが有効になっていることを確認します。 そうでない場合は、 **[名前付きパイプ]** を右クリックし、 **[有効]** をクリックします。  
  
     サービスの停止および再起動が必要になります。 次のブロックの手順に従って操作します。  
  
### <a name="stopping-and-restarting-the-service"></a>サービスの停止および再起動  
 変更を有効にするには、サービスを停止し、再起動する必要があります。  
  
##### <a name="to-stop-and-restart-the-service"></a>サービスを停止および再起動するには  
  
1. **SQL Server 構成マネージャー**の左ペインで、 **[SQL Server 2005 サービス]** をクリックします。  
  
2. 右ペインで、 **[SQL Server (SQLEXPRESS)]** を右クリックし、 **[停止]** をクリックします。  
  
3. **[SQL Server (SQLEXPRESS)]** を右クリックし、 **[再起動]** をクリックします。  
  
## <a name="see-also"></a>関連項目

- [はじめに](getting-started.md)
