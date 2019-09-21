---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: 12255f738dea0a4713389e599468d1a7fab67d23
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784693"
---
# <a name="datatables"></a>DataTables
<xref:System.Data.DataSet> は、テーブル、リレーションシップ、および制約のコレクションで構成されます。 ADO.NET では<xref:System.Data.DataTable> 、オブジェクトは**データセット**内のテーブルを表すために使用されます。 **DataTable**は、インメモリリレーショナルデータの1つのテーブルを表します。データはに対してローカルです。ネットワークベースのアプリケーションが存在しますが、 **dataadapter**を使用した Microsoft SQL Server などのデータソースからデータを設定できます。詳細については、「 [Dataadapter からのデータセットの読み込み](../populating-a-dataset-from-a-dataadapter.md)」を参照してください。  
  
 **DataTable**クラスは、.NET Framework クラスライブラリ内の**system.string 名前空間**のメンバーです。 **Datatable**は、**データセット**のメンバーとして個別に作成および使用できます。また、 **datatable**オブジェクトは、 <xref:System.Data.DataView>などの他の .NET Framework オブジェクトと組み合わせて使用することもできます。 **Dataset オブジェクトの** **tables**プロパティを使用して、**データセット**内のテーブルのコレクションにアクセスします。  
  
 テーブルのスキーマ (構造) は、列と制約で表されます。 オブジェクトとオブジェクト<xref:System.Data.DataColumn> および<xref:System.Data.UniqueConstraint>オブジェクトを使用して、DataTable のスキーマを定義します。 <xref:System.Data.ForeignKeyConstraint> テーブルの列は、データ ソースの列に割り当てたり、式で算出された値を格納したり、格納されている値を自動的にインクリメントしたり、主キー値を格納したりできます。  
  
 スキーマに加えて、 **DataTable**には、データを格納および順序付けるための行も必要です。 <xref:System.Data.DataRow> クラスは、テーブルに格納される実際のデータを表します。 **DataRow**とそのプロパティとメソッドを使用して、テーブル内のデータを取得、評価、および操作します。 行内のデータにアクセスして変更すると、 **DataRow**オブジェクトは現在の状態と元の状態の両方を保持します。  
  
 テーブル間で 1 つ以上の列を関連付け、テーブル間の親子のリレーションシップを作成できます。 **DataTable**オブジェクト間のリレーションシップを作成するに<xref:System.Data.DataRelation>は、を使用します。 **DataRelation**オブジェクトを使用して、特定の行の関連する子行または親行を返すことができます。 詳細については、「 [datarelation の追加](adding-datarelations.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataTable の作成](creating-a-datatable.md)  
 **DataTable**を作成して**データセット**に追加する方法について説明します。  
  
 [DataTable スキーマの定義](datatable-schema-definition.md)  
 **DataColumn**オブジェクトと制約の作成と使用に関する情報を提供します。  
  
 [DataTable 内のデータの操作](manipulating-data-in-a-datatable.md)  
 テーブル内のデータを追加、変更、および削除する方法について説明します。 **DataTable**イベントを使用して、テーブル内のデータに対する変更を確認する方法について説明します。  
  
 [DataTable イベントの処理](handling-datatable-events.md)  
 列の値が変更され、行が追加または削除された場合のイベントなど、 **DataTable**で使用できるイベントに関する情報を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [ADO.NET](../index.md)  
 ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。  
  
 [DataSet、DataTable、および DataView](index.md)  
 テーブル間のリレーションシップを作成する方法など、ADO.NET**データセット**に関する情報を提供します。  
  
 <xref:System.Data.Constraint>  
 **制約**オブジェクトに関する参照情報を提供します。  
  
 <xref:System.Data.DataColumn>  
 **DataColumn**オブジェクトに関する参照情報を提供します。  
  
 <xref:System.Data.DataSet>  
 **DataSet**オブジェクトに関する参照情報を提供します。  
  
 <xref:System.Data.DataTable>  
 **DataTable**オブジェクトに関する参照情報を提供します。  
  
 [.NET クラス ライブラリの概要](../../../../standard/class-library-overview.md)  
 **System**名前空間と、その第2レベルの名前**空間である**system.string を含む .NET Framework クラスライブラリの概要について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)
