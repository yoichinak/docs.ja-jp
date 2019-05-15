---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: ef95a7cebb527b01c15d124227664823fcbbaa23
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582778"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .NET Framework version 3.5 オブジェクトとしてのリレーショナル データを管理するためのランタイム インフラストラクチャを提供するコンポーネントです。  
  
> [!NOTE]
>  リレーショナル データは 2 次元テーブル (*リレーション*または*フラット ファイル*) のコレクションで表され、共通の列がテーブルを相互に関連付けます。 
  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を効果的に使用するには、リレーショナル データベースの基本原則を理解している必要があります。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。 アプリケーションが実行されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。 データベースから結果が返されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はそれをプログラミング言語で操作できるオブジェクトに変換し直します。  
  
 通常 Visual Studio を使用している開発者が使用して、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]の機能の多くを実装するためのユーザー インターフェイスを提供する[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]します。  
  
 このリリースの [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に含まれているドキュメントでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを構築するのに必要な基本的なビルド ブロック、プロセス、および手法について説明します。 特定の問題に関する Microsoft のドキュメントを検索することとに参加することができます、 [LINQ フォーラム](https://go.microsoft.com/fwlink/?LinkId=76488)専門家とより複雑なトピックを説明できます。 最後に、 [LINQ to SQL: リレーショナル データ用 .net 統合言語クエリ](https://go.microsoft.com/fwlink/?LinkId=93205)ホワイト ペーパーの詳細[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]テクノロジ、Visual Basic と c# のコード例を完了します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の簡単な概要と、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して作業を始める方法を示します。  
  
 [プログラミング ガイド](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 マップ、クエリ、更新、デバッグ、および同様のタスクを行う手順を示します。  
  
 [参照](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 
  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のさまざまな側面に関するリファレンス情報を示します。 SQL-CLR 型マッピング、標準クエリ演算子変換などのトピックが含まれます。  
  
 [サンプル](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 Visual Basic および c# のサンプルへのリンクを提供します。  
  
## <a name="related-sections"></a>関連項目  
 [統合言語クエリ (LINQ)C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 LINQ テクノロジの概要について説明しますC#します。
 
 [統合言語クエリ (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Visual Basic での LINQ テクノロジの概要について説明します。
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 説明[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]Visual Basic ユーザー向けのテクノロジです。  
  
 [LINQ と ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 
  [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] ポータルにリンクします。  
  
 [LINQ to SQL チュートリアル](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 
  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のチュートリアルを一覧します。  
  
 [サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 ドキュメントで使用されるサンプル データベースをダウンロードする方法について説明します。  
  
 [LinqDataSource Web サーバー コントロールの概要](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 
  <xref:System.Web.UI.WebControls.LinqDataSource> コントロールが [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] データソース コントロールのアーキテクチャを通じて[!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] を Web 開発者に公開する方法について説明します。
