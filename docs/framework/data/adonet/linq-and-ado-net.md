---
title: LINQ と ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: 9c517b3efca8cd2b41782858ef1e18e3cba76c1b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539408"
---
# <a name="linq-and-adonet"></a>LINQ と ADO.NET
今日では、多くのビジネス開発者が 2 つ (以上) のプログラミング言語を使用する必要がありますビジネス ロジックやプレゼンテーション層は高級言語 (Visual などC#または Visual Basic)、および (TRANSACT-SQL) などのデータベースと対話するクエリ言語. 開発者は実質的に複数の言語に精通していることが要求され、開発環境における言語の不整合が生じる原因にもなっています。 たとえば、データ アクセス API を使用してデータベースを照会するアプリケーションでは、クエリは文字列リテラルとして引用符で囲んで指定する必要があります。 コンパイラはこのクエリ文字列を認識できないため、エラー (無効な構文、参照されている列または行が実際に存在するかどうかなど) のチェック機構が働きません。 クエリ パラメーターの型チェックや `IntelliSense` のサポートもありません。  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] により、開発者はアプリケーション コード内でプログラミング言語とクエリ言語を使い分けることなく、セット ベースのクエリを作成できます。 インメモリのデータ構造、XML ドキュメント、SQL データベース、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] オブジェクトなど、列挙可能な各種データ ソース (つまり、<xref:System.Collections.IEnumerable> インターフェイスを実装するデータ ソース) に対する <xref:System.Data.DataSet> クエリを作成できます。 実装方法には違いがありますが、こうした列挙可能なデータ ソースはすべて同じ構文および言語構造を公開しています。 クエリはプログラミング言語のみで作成できるため、コンパイラによる認識も検証もできない文字列リテラルとしてクエリ言語を記述する必要はありません。 Visual Studio プログラマはコンパイル時の型や構文チェックを提供することで生産性を向上させることもできますクエリをプログラミング言語に統合し、`IntelliSense`します。 クエリのデバッグやエラーの修正に伴う手間は、これらの機能によって軽減されます。  
  
 SQL テーブルのデータをメモリ内のオブジェクトに転送することは、面倒であるだけでなく間違いの元にもなります。 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] LINQ to DataSet によって実装されるプロバイダーと[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]にソース データを変換<xref:System.Collections.IEnumerable>-ベースのオブジェクトのコレクション。 プログラマからは、クエリの実行時も更新時も常にデータが <xref:System.Collections.IEnumerable> コレクションとして見えます。 これらのコレクションに対するクエリを記述する際には、`IntelliSense` の機能を完全に利用できます。  
  
 次の 3 つの別個の ADO.NET[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]テクノロジ。LINQ to DataSet、 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]、および LINQ to Entities。 LINQ to DataSet の提供に対するクエリの実行度で最適化された、<xref:System.Data.DataSet>と[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]できるように Entity Data Model のクエリを直接 SQL Server データベースのスキーマ、および LINQ to Entities クエリを実行することができます。  
  
 次の図は、ADO.NET LINQ テクノロジが、高級プログラミング言語および LINQ 対応のデータ ソースとどのように関係しているかを簡単に表したものです。  
  
 ![LINQ to ADO.NET overview](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 LINQ の詳細については、次を参照してください。[言語統合クエリ (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)します。
  
 次のセクションでは、データセットに LINQ の詳細についてを提供する[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]、および LINQ to Entities。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> ADO.NET は、上に構築し、広く使用されている非接続型プログラミング モデルの重要な要素です。 豊富なクエリ機能を構築する開発者は LINQ to DataSet<xref:System.Data.DataSet>他の多くのデータ ソースに使用される同じクエリ定式化メカニズムを使用します。 詳細については、「[LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] は、概念モデルへのマッピングを必要としない開発者にとって有用なツールです。 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] では、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] プログラミング モデルを既存のデータベース スキーマ上で直接利用できるようになります。 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] データを表す .NET Framework クラスを生成することができます。 こうして生成されたクラスは、概念データ モデルではなく、直接データベースのテーブル、ビュー、ストアド プロシージャ、およびユーザー定義関数にマッピングされます。  
  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] では、開発者が、XML などのデータ ソースに加え、インメモリ コレクションや [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] と同じ <xref:System.Data.DataSet> プログラミング パターンを使用して、ストレージ スキーマに対して直接コードを記述できます。 詳細については、「[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)」を参照してください。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 現在、多くのアプリケーションが、リレーショナル データベースを基にして作成されています。 ある時点で、これらのアプリケーションにはリレーショナル形式で表されるデータと対話する必要が生じます。 データベース スキーマはアプリケーションの構築に理想的であるとは限らず、アプリケーションの概念モデルはデータベースの論理モデルと同じではありません。 Entity Data Model は、アプリケーションでデータをオブジェクトとして操作できるように、特定のドメインのデータをモデル化に使用できる概念データ モデルです。 参照してください[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)詳細についてはします。  
  
 Entity Data Model では、リレーショナル データが .NET 環境にオブジェクトとして公開されます。 これにより、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。 この機能は、エンティティに、LINQ と呼ばれます。 LINQ の詳細については、「[LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)
- [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [統合言語クエリ (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET の概要](ado-net-overview.md)
