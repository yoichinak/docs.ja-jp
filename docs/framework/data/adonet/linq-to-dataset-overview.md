---
title: LINQ to DataSet の概要
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: 635f1c17da40095990c238912f9e09ad398e6637
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878593"
---
# <a name="linq-to-dataset-overview"></a>LINQ to DataSet の概要
<xref:System.Data.DataSet> は、[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] のコンポーネントの中でもきわめて使用頻度の高いコンポーネントの 1 つです。 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] の基礎を成す非接続型プログラミング モデルの重要な要素であり、さまざまなデータ ソースからのデータを明示的にキャッシュできます。 プレゼンテーション層では、<xref:System.Data.DataSet> とデータ バインディングの GUI コントロールとが密接に連携します。 中間層では、リレーショナル形式のデータを維持するキャッシュとして機能し、単純で高速なクエリと、階層的なナビゲーション サービスを提供します。 データベースに対する要求の数を削減するために使用する一般的な手法は、使用する、<xref:System.Data.DataSet>中間層でのキャッシュします。 たとえば、データ ドリブン[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web アプリケーション。 ほとんど変更されないアプリケーション データがかなりの割合で存在し、しかも、複数のセッションまたは複数のユーザー間で共通して使用されているケースがよくあります。 このデータを Web サーバー上のメモリに維持しておくことで、データベースに対する要求数を減らし、高速な対話処理をユーザーに提供できます。 もう 1 つの便利な側面、<xref:System.Data.DataSet>アプリケーション領域に 1 つまたは複数のデータ ソースからデータのサブセットをアプリケーションでできることです。 アプリケーションは、そのデータをリレーショナル形式を維持したままインメモリで操作できます。  
  
 こうした突出した特長がある反面、<xref:System.Data.DataSet> のクエリ機能には制限があります。 <xref:System.Data.DataTable.Select%2A> メソッドでデータのフィルター処理や並べ替えを行ったり、<xref:System.Data.DataRow.GetChildRows%2A> メソッドや <xref:System.Data.DataRow.GetParentRow%2A> メソッドを使って階層のナビゲーションを行うことはできます。 しかし、さらに複雑な処理を行うには、開発者が独自にクエリを作成する必要があります。 その結果、アプリケーションで期待したパフォーマンスが得られなかったり、メンテナンスが難しくなったりする可能性があります。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] は、<xref:System.Data.DataSet> オブジェクトにキャッシュされたデータに対するクエリをより簡単に、より高速にします。 これらのクエリはアプリケーション コードに文字列リテラルとして記述するのではなく、プログラミング言語そのもので表現できます。 つまり、開発者はクエリ言語を個別に習得する必要はありません。 さらに、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]により、Visual Studio IDE は、コンパイル時の構文チェック、静的な型指定、および IntelliSense サポートを提供するために Visual Studio 開発者はより生産的に作業を[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]します。 また、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使用すると、1 つまたは複数のデータ ソースから取得して統合したデータを照会することもできます。 これにより、データの表現方法や扱いに柔軟性が要求されるさまざまなシナリオが実現します。 特に、汎用のレポート作成、分析、ビジネス インテリジェンスを行うアプリケーションでは、この手法を用いたデータ操作が欠かせません。  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>LINQ to DataSet を使った DataSet のクエリ  
 <xref:System.Data.DataSet> を使用して [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] オブジェクトを照会するには、あらかじめ <xref:System.Data.DataSet> にデータを読み込んでおく必要があります。 いくつかの方法にデータを読み込む、<xref:System.Data.DataSet>などを使用して、<xref:System.Data.Common.DataAdapter>クラスまたは[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)します。 データが読み込まれた後、<xref:System.Data.DataSet>オブジェクト、クエリを実行を開始することができます。 使用してクエリを作成[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]使用と似ています[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]他に対して[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-データ ソースを有効にします。 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 単一テーブルに対してクエリを実行できる、<xref:System.Data.DataSet>またはを使用して 1 つ以上のテーブルに対して、<xref:System.Linq.Enumerable.Join%2A>と<xref:System.Linq.Enumerable.GroupJoin%2A>標準クエリ演算子。  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 型指定された、型指定されていないとの両方に対してクエリがサポートされている<xref:System.Data.DataSet>オブジェクト。 アプリケーションのデザイン時に <xref:System.Data.DataSet> のスキーマがわかっている場合は、型指定された <xref:System.Data.DataSet> を使用することをお勧めします。 型指定された <xref:System.Data.DataSet> のテーブルおよび行は、列ごとに型指定されたメンバーを持ちます。これにより、クエリが簡素化され、読みやすくなります。  
  
 だけでなく、System.Core.dll に実装された標準クエリ演算子[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]いくつか追加<xref:System.Data.DataSet>-特定の拡張機能のセットに対してクエリを簡単にする<xref:System.Data.DataRow>オブジェクト。 これらの <xref:System.Data.DataSet> 固有の拡張機能には、<xref:System.Data.DataRow> の列値にアクセスするためのメソッドのほか、一連の行を比較するための演算子があります。  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>n 層アプリケーションと LINQ to DataSet  
 n 層データ アプリケーションは、複数の論理レイヤー (層) に分けられた、データ処理を中心とするアプリケーションです。 一般に、n 層アプリケーションには、プレゼンテーション層、中間層、およびデータ層が含まれます。 アプリケーション コンポーネントを別個の層に分離すると、アプリケーションの保守容易性とスケーラビリティが向上します。 N 層データ アプリケーションの詳細については、次を参照してください。 [n 層アプリケーションでデータセットを操作](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)します。  
  
 n 層アプリケーションでは、Web アプリケーションの情報をキャッシュするために <xref:System.Data.DataSet> が中間層で使用されます。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ機能は拡張メソッドによって実装され、既存の ADO.NET 2.0 の拡張<xref:System.Data.DataSet>します。  
  
## <a name="see-also"></a>関連項目

- [DataSet のクエリ](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [統合言語クエリ (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [統合言語クエリ (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
