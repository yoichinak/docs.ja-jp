---
title: データ バインディングと LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: b081a648023aa21eea3a20ec409600d3bcbe9878
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607402"
---
# <a name="data-binding-and-linq-to-dataset"></a>データ バインディングと LINQ to DataSet
*データ バインディング*はアプリケーションの UI とビジネス ロジックの間の接続を確立するプロセスです。 バインドが適切に設定され、データから適切な通知が提供される場合、データの値が変更されると、そのデータにバインドされている要素に変更が自動的に反映されます。 <xref:System.Data.DataSet> はメモリ内データ表現であり、含まれているデータ ソースとは関係なく、一貫性のあるリレーショナル プログラミング モデルを提供します。 ADO.NET 2.0 の <xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータの並べ替えとフィルター処理を行うことができます。 この機能は、データ バインディング アプリケーションで一般に使用されます。 <xref:System.Data.DataView> を使用すると、さまざまな並べ替え順序を使用してテーブルのデータを公開したり、行の状態やフィルター式に基づいてデータをフィルター処理したりできます。 詳細については、<xref:System.Data.DataView>オブジェクトを参照してください[Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)します。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] により、開発者は複雑で強力なクエリを作成する、<xref:System.Data.DataSet>を使用して[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]します。 ただし、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリの列挙を返します<xref:System.Data.DataRow>バインディングのシナリオで簡単に使用されていないオブジェクト。 バインドを簡単にするには、作成することができます、<xref:System.Data.DataView>から、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。 これは、<xref:System.Data.DataView>フィルター処理とクエリで指定した並べ替えを使用しますが、データ バインディングがやりやすくなります。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 機能を拡張、<xref:System.Data.DataView>により[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]式ベースのフィルター処理と並べ替え、はるかに複雑で強力なフィルター処理と並べ替え文字列ベースのフィルター処理と並べ替えよりも操作できます。  
  
 <xref:System.Data.DataView> はクエリ自体を表すもので、クエリに基づくビューではありません。 単純なデータ バインディング モデルを提供する場合、<xref:System.Data.DataView> は、<xref:System.Windows.Forms.DataGrid> や <xref:System.Windows.Forms.DataGridView> などの UI コントロールにバインドされます。 当該テーブルの既定のビューを提供する場合、<xref:System.Data.DataView> は、<xref:System.Data.DataTable> から作成することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataView オブジェクトの作成](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 <xref:System.Data.DataView> の作成に関する情報を提供します。  
  
 [DataView によるフィルター処理](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 <xref:System.Data.DataView> を使用してフィルター処理する方法について説明します。  
  
 [DataView による並べ替え](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 <xref:System.Data.DataView> を使用して並べ替えを行う方法について説明します。  
  
 [DataView の DataRowView コレクションの照会](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 <xref:System.Data.DataRowView> が公開する <xref:System.Data.DataView> コレクションを照会する方法について説明します。  
  
 [DataView のパフォーマンス](../../../../docs/framework/data/adonet/dataview-performance.md)  
 <xref:System.Data.DataView> およびパフォーマンスに関する情報を提供します。  
  
 [方法: DataView オブジェクトを Windows フォームの DataGridView コントロールにバインドします。](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 <xref:System.Data.DataView> オブジェクトを <xref:System.Windows.Forms.DataGridView> にバインドする方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [プログラミング ガイド](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
