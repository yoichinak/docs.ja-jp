---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: b0660312f540a69911905edd08541ed70cf39bb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174317"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]は、リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャを提供する .NET Framework Version 3.5 のコンポーネントです。  
  
> [!NOTE]
> リレーショナル データは 2 次元テーブル (*リレーション*または*フラット ファイル*) のコレクションで表され、共通の列がテーブルを相互に関連付けます。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を効果的に使用するには、リレーショナル データベースの基本原則を理解している必要があります。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。 アプリケーションが実行されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。 データベースから結果が返されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はそれをプログラミング言語で操作できるオブジェクトに変換し直します。  
  
 Visual Studio を使用する開発者は通常、オブジェクト リレーショナル デザイナーを使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]します。  
  
 このリリースの [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に含まれているドキュメントでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを構築するのに必要な基本的なビルド ブロック、プロセス、および手法について説明します。 また、Microsoft Docs で特定の問題を検索したり、さらに複雑なトピックについて専門家と詳しく議論できる[LINQ フォーラム](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)に参加することもできます。 最後に、 [LINQ to SQL: .NET リレーショナル データの統合クエリ](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10))の詳細に[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]関する技術を Visual Basic と C# のコード例を含みます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](getting-started.md)  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の簡単な概要と、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して作業を始める方法を示します。  
  
 [プログラミング ガイド](programming-guide.md)  
 マップ、クエリ、更新、デバッグ、および同様のタスクを行う手順を示します。  
  
 [リファレンス](reference.md)  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のさまざまな側面に関するリファレンス情報を示します。 SQL-CLR 型マッピング、標準クエリ演算子変換などのトピックが含まれます。  
  
 [サンプル](samples.md)  
 Visual Basic および C# のサンプルへのリンクを提供します。  
  
## <a name="related-sections"></a>関連項目  
 [言語統合クエリ (LINQ) - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 C# での LINQ テクノロジの概要について説明します。

 [統合言語クエリ (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 VISUAL Basic での LINQ テクノロジの概要について説明します。
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Visual Basic ユーザー向けの LINQ テクノロジについて説明します。  
  
 [LINQ と ADO.NET](../../linq-and-ado-net.md)  
 ADO.NET ポータルへのリンク。  
  
 [LINQ to SQL チュートリアル](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のチュートリアルを一覧します。  
  
 [サンプル データベースのダウンロード](downloading-sample-databases.md)  
 ドキュメントで使用されるサンプル データベースをダウンロードする方法について説明します。  
  
 [Web サーバー コントロールの概要](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 ASP.NETデータ ソース<xref:System.Web.UI.WebControls.LinqDataSource>コントロール アーキテクチャを通じて、Web 開発者に対してコントロールが統合言語クエリ (LINQ) を公開する方法について説明します。
