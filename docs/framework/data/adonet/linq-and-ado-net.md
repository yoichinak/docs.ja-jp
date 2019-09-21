---
title: LINQ と ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: d354e2e7f2696e90845edf0348340986fd7bb83c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795193"
---
# <a name="linq-and-adonet"></a>LINQ と ADO.NET
現在、多くのビジネス開発者は、2つ (またはそれ以上) のプログラミング言語を使用する必要があります。ビジネスロジックとC#プレゼンテーション層の高水準言語 (Visual や Visual Basic など) と、データベースと対話するためのクエリ言語 (transact-sql など) です. 開発者は実質的に複数の言語に精通していることが要求され、開発環境における言語の不整合が生じる原因にもなっています。 たとえば、データ アクセス API を使用してデータベースを照会するアプリケーションでは、クエリは文字列リテラルとして引用符で囲んで指定する必要があります。 コンパイラはこのクエリ文字列を認識できないため、エラー (無効な構文、参照されている列または行が実際に存在するかどうかなど) のチェック機構が働きません。 クエリ パラメーターの型チェックや `IntelliSense` のサポートもありません。  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] により、開発者はアプリケーション コード内でプログラミング言語とクエリ言語を使い分けることなく、セット ベースのクエリを作成できます。 インメモリのデータ構造、XML ドキュメント、SQL データベース、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] オブジェクトなど、列挙可能な各種データ ソース (つまり、<xref:System.Collections.IEnumerable> インターフェイスを実装するデータ ソース) に対する <xref:System.Data.DataSet> クエリを作成できます。 実装方法には違いがありますが、こうした列挙可能なデータ ソースはすべて同じ構文および言語構造を公開しています。 クエリはプログラミング言語のみで作成できるため、コンパイラによる認識も検証もできない文字列リテラルとしてクエリ言語を記述する必要はありません。 クエリをプログラミング言語に統合することにより、コンパイル時の型と構文チェック、および`IntelliSense`を提供することで、Visual Studio プログラマの生産性を向上させることができます。 クエリのデバッグやエラーの修正に伴う手間は、これらの機能によって軽減されます。  
  
 SQL テーブルのデータをメモリ内のオブジェクトに転送することは、面倒であるだけでなく間違いの元にもなります。 LINQ to DataSet によって実装さ[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]れた<xref:System.Collections.IEnumerable>プロバイダー。ソースデータをベースのオブジェクトコレクションに[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]変換します。 プログラマからは、クエリの実行時も更新時も常にデータが <xref:System.Collections.IEnumerable> コレクションとして見えます。 これらのコレクションに対するクエリを記述する際には、`IntelliSense` の機能を完全に利用できます。  
  
 ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] には、3 つのテクノロジがあります。LINQ to DataSet、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]、LINQ to Entities です。 LINQ to DataSet は、に対してより高度<xref:System.Data.DataSet>で[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]最適化されたクエリを提供し、SQL Server データベーススキーマに直接クエリを実行できるようにします。また LINQ to Entities では、Entity Data Model に対してクエリを実行できます。  
  
 次の図は、ADO.NET LINQ テクノロジが、高級プログラミング言語および LINQ 対応のデータ ソースとどのように関係しているかを簡単に表したものです。  
  
 ![LINQ to ADO.NET の概要](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 LINQ の詳細については、「[統合言語クエリ (linq)](../../../csharp/programming-guide/concepts/linq/index.md)」を参照してください。
  
 次のセクションでは、LINQ to DataSet、 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]、および LINQ to Entities の詳細について説明します。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet>は、ADO.NET が構築される非接続型プログラミングモデルの重要な要素であり、広く使用されています。 LINQ to DataSet を使用すると、開発者は<xref:System.Data.DataSet> 、他の多くのデータソースで使用できるのと同じクエリ定式化メカニズムを使用して、豊富なクエリ機能をに組み込むことができます。 詳細については、「[LINQ to DataSet](linq-to-dataset.md)」を参照してください。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] は、概念モデルへのマッピングを必要としない開発者にとって有用なツールです。 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] では、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] プログラミング モデルを既存のデータベース スキーマ上で直接利用できるようになります。 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]開発者がデータを表す .NET Framework クラスを生成できるようにします。 こうして生成されたクラスは、概念データ モデルではなく、直接データベースのテーブル、ビュー、ストアド プロシージャ、およびユーザー定義関数にマッピングされます。  
  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] では、開発者が、XML などのデータ ソースに加え、インメモリ コレクションや [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] と同じ <xref:System.Data.DataSet> プログラミング パターンを使用して、ストレージ スキーマに対して直接コードを記述できます。 詳細については、「[LINQ to SQL](./sql/linq/index.md)」を参照してください。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 現在、多くのアプリケーションが、リレーショナル データベースを基にして作成されています。 ある時点で、これらのアプリケーションにはリレーショナル形式で表されるデータと対話する必要が生じます。 データベース スキーマはアプリケーションの構築に理想的であるとは限らず、アプリケーションの概念モデルはデータベースの論理モデルと同じではありません。 Entity Data Model は、アプリケーションがデータをオブジェクトとして操作できるように、特定のドメインのデータをモデル化するために使用できる概念データモデルです。 詳細については、「 [ADO.NET Entity Framework](./ef/index.md) 」を参照してください。  
  
 Entity Data Model では、リレーショナル データが .NET 環境にオブジェクトとして公開されます。 これにより、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。 この機能は、LINQ to Entities と呼ばれます。 LINQ の詳細については、「[LINQ to Entities](./ef/language-reference/linq-to-entities.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [統合言語クエリ (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET の概要](ado-net-overview.md)
