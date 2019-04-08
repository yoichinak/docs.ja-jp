---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: f0f429d7f28360fd76dfff0e7d4a4eba019e5acf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653251"
---
# <a name="datatables"></a>DataTables
<xref:System.Data.DataSet> は、テーブル、リレーションシップ、および制約のコレクションで構成されます。 ADO.NET では、<xref:System.Data.DataTable>オブジェクトは、テーブルを表すために使用する**データセット**します。 A **DataTable**リレーショナル データをメモリ内の 1 つのテーブルを表すデータがローカルにします。NET ベースのアプリケーションが存在するを使用して Microsoft SQL Server などのデータ ソースからデータを読み込むことができます、 **DataAdapter**詳細については、次を参照してください[DataAdapter からの Dataset](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .  
  
 **DataTable**クラスのメンバーである、 **System.Data** .NET Framework クラス ライブラリ内の名前空間。 作成して使用することができます、 **DataTable**とは独立してまたはのメンバーとして、**データセット**、および**DataTable**オブジェクトは、その他の .NET Framework のオブジェクトと組み合わせても使用できますなど、<xref:System.Data.DataView>します。 内のテーブルのコレクションにアクセスする、**データセット**を通じて、**テーブル**のプロパティ、**データセット**オブジェクト。  
  
 テーブルのスキーマ (構造) は、列と制約で表されます。 スキーマを定義する、 **DataTable**を使用して<xref:System.Data.DataColumn>オブジェクトだけでなく<xref:System.Data.ForeignKeyConstraint>と<xref:System.Data.UniqueConstraint>オブジェクト。 テーブルの列は、データ ソースの列に割り当てたり、式で算出された値を格納したり、格納されている値を自動的にインクリメントしたり、主キー値を格納したりできます。  
  
 スキーマだけでなく、 **DataTable**行が含まれており、データを注文する必要があります。 <xref:System.Data.DataRow> クラスは、テーブルに格納される実際のデータを表します。 使用する、 **DataRow**とそのプロパティとメソッドを取得するには、評価、およびテーブルにデータを操作します。 アクセスして、行内のデータを変更すると、 **DataRow**オブジェクトは、両方の現在と元の状態を維持します。  
  
 テーブル間で 1 つ以上の列を関連付け、テーブル間の親子のリレーションシップを作成できます。 間のリレーションシップを作成する**DataTable**オブジェクトを使用して、<xref:System.Data.DataRelation>します。 **DataRelation**オブジェクトは、特定の行の関連子または親の行を取得し、使用できます。 詳細については、[Datarelation の追加](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataTable の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 作成する方法について説明します、 **DataTable**に追加し、**データセット**します。  
  
 [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 作成と使用に関する情報を提供**DataColumn**オブジェクトと制約。  
  
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 テーブル内のデータを追加、変更、および削除する方法について説明します。 使用する方法について説明します**DataTable**テーブル内のデータへの変更を確認するイベントです。  
  
 [DataTable イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 使用するために使用できるイベントに関する情報を提供する**DataTable**列の値が変更され、行を追加または削除されたときにイベントが含まれます。  
  
## <a name="related-sections"></a>関連項目  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。  
  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 ADO.NET についての情報を提供します**データセット**テーブル間のリレーションシップを作成する方法などです。  
  
 <xref:System.Data.Constraint>  
 参照情報を提供、**制約**オブジェクト。  
  
 <xref:System.Data.DataColumn>  
 参照情報を提供、 **DataColumn**オブジェクト。  
  
 <xref:System.Data.DataSet>  
 参照情報を提供、**データセット**オブジェクト。  
  
 <xref:System.Data.DataTable>  
 参照情報を提供、 **DataTable**オブジェクト。  
  
 [クラス ライブラリの概要](../../../../../docs/standard/class-library-overview.md)  
 .NET Framework クラス ライブラリの概要を説明など、**システム**名前空間、2 番目のレベルの名前空間と**System.Data**。  
  
## <a name="see-also"></a>関連項目
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
