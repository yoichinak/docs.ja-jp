---
title: データ バインディングと LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 563d57249daa3aa720da1d9654866727f770afb3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786705"
---
# <a name="data-binding-and-linq-to-dataset"></a>データ バインディングと LINQ to DataSet
*データバインディング*は、アプリケーション UI とビジネスロジックの間の接続を確立するプロセスです。 バインドが適切に設定され、データから適切な通知が提供される場合、データの値が変更されると、そのデータにバインドされている要素に変更が自動的に反映されます。 <xref:System.Data.DataSet> はメモリ内データ表現であり、含まれているデータ ソースとは関係なく、一貫性のあるリレーショナル プログラミング モデルを提供します。 ADO.NET 2.0 の <xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータの並べ替えとフィルター処理を行うことができます。 この機能は、データ バインディング アプリケーションで一般に使用されます。 <xref:System.Data.DataView> を使用すると、さまざまな並べ替え順序を使用してテーブルのデータを公開したり、行の状態やフィルター式に基づいてデータをフィルター処理したりできます。 オブジェクトの<xref:System.Data.DataView>詳細については、「 [dataviews](./dataset-datatable-dataview/dataviews.md)」を参照してください。  
  
 LINQ to DataSet を使用すると、開発者はを使用<xref:System.Data.DataSet> [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]して、に対する複雑で強力なクエリを作成できます。 ただし、LINQ to DataSet クエリは、バインディングシナリオで<xref:System.Data.DataRow>は簡単に使用できないオブジェクトの列挙体を返します。 バインドを容易にするために、LINQ to DataSet <xref:System.Data.DataView>クエリからを作成できます。 これ<xref:System.Data.DataView>は、クエリで指定されたフィルター処理と並べ替えを使用しますが、データバインディングに適しています。 LINQ to DataSet は、式ベースの<xref:System.Data.DataView>フィルター処理[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]と並べ替えを提供することで、の機能を拡張します。これにより、文字列ベースのフィルター処理や並べ替えよりもはるかに複雑で強力なフィルター処理と並べ替え操作が可能になります。  
  
 <xref:System.Data.DataView> はクエリ自体を表すもので、クエリに基づくビューではありません。 単純なデータ バインディング モデルを提供する場合、<xref:System.Data.DataView> は、<xref:System.Windows.Forms.DataGrid> や <xref:System.Windows.Forms.DataGridView> などの UI コントロールにバインドされます。 当該テーブルの既定のビューを提供する場合、<xref:System.Data.DataView> は、<xref:System.Data.DataTable> から作成することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataView オブジェクトの作成](creating-a-dataview-object-linq-to-dataset.md)  
 <xref:System.Data.DataView> の作成に関する情報を提供します。  
  
 [DataView によるフィルター処理](filtering-with-dataview-linq-to-dataset.md)  
 <xref:System.Data.DataView> を使用してフィルター処理する方法について説明します。  
  
 [DataView による並べ替え](sorting-with-dataview-linq-to-dataset.md)  
 <xref:System.Data.DataView> を使用して並べ替えを行う方法について説明します。  
  
 [DataView の DataRowView コレクションの照会](querying-the-datarowview-collection-in-a-dataview.md)  
 <xref:System.Data.DataRowView> が公開する <xref:System.Data.DataView> コレクションを照会する方法について説明します。  
  
 [DataView のパフォーマンス](dataview-performance.md)  
 <xref:System.Data.DataView> およびパフォーマンスに関する情報を提供します。  
  
 [方法: DataView オブジェクトを Windows フォーム DataGridView コントロールにバインドする](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 <xref:System.Data.DataView> オブジェクトを <xref:System.Windows.Forms.DataGridView> にバインドする方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [プログラミング ガイド](programming-guide-linq-to-dataset.md)
