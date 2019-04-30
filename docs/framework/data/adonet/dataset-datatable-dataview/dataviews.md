---
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: aff4d6f648fa091130bfd9951f2a5001947b09a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034334"
---
# <a name="dataviews"></a>DataView
<xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータのさまざまなビューを作成できます。この機能は、データ連結アプリケーションで頻繁に使用されます。 使用して、 **DataView**、さまざまな並べ替え順序、テーブル内のデータを公開して、によって行の状態やフィルター式に基づいてデータをフィルター処理できます。  
  
 A **DataView** 、基になるデータの動的なビューを提供します。 **DataTable**: コンテンツ、並べ替え、およびメンバーシップ発生時に変更を反映します。 この動作は異なります、**選択**のメソッド、 **DataTable**、返された、<xref:System.Data.DataRow>特定のフィルターまたは並べ替え順序に基づいて、テーブルからの配列: このコンテンツへの変更が反映されます、テーブルが、メンバーシップを基になると、順序付けは、静的なままです。 動的機能、 **DataView**データ バインド アプリケーションに最適です。  
  
 A **DataView**では、さまざまな並べ替えやフィルター処理条件を適用できる、データベース ビューと同様に、データの 1 つのセットの動的な表示。 ただし、データベース ビューとは異なり、 **DataView**テーブルとして扱うことはできませんし、結合テーブルのビューを提供することはできません。 また、ソース テーブルの既存の列を除外したり、ソース テーブルにない列 (計算列など) を追加することはできません。  
  
 使用することができます、<xref:System.Data.DataView.DataViewManager%2A>内のすべてのテーブルの表示設定を管理する、**データセット**します。 **DataViewManager**の各テーブルの既定のビュー設定を管理する便利な方法です。 1 つ以上のテーブルにコントロールをバインドするときに、**データセット**連結する、 **DataViewManager**は理想的な選択肢です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataView の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 作成する方法について説明します、 **DataView**の**DataTable**します。  
  
 [データの並べ替えとフィルター処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 プロパティを設定する方法について説明します、 **DataView**特定のフィルター条件を満たす、データ行のサブセットを返すか、特定の並べ替え順序でデータを返します。  
  
 [DataRow および DataRowView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 によって公開されているデータにアクセスする方法について説明します、 **DataView**します。  
  
 [行の検索](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 特定の行を検索する方法について説明します、 **DataView**します。  
  
 [ChildView とリレーション](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 使用して、親子リレーションシップからデータのビューを作成する方法について説明します、 **DataView**します。  
  
 [DataView の変更](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 基になるデータを変更する方法について説明します**DataTable**を使用して、 **DataView**などを有効にするまたは更新プログラムを無効にします。  
  
 [DataView イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 使用する方法について説明します、 **ListChanged**イベント通知を受信するときに内容またはの順序を**DataView**が更新されています。  
  
 [DataViews の管理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 使用する方法について説明します、 **DataViewManager**を管理する**DataView**内の各テーブルの設定、**データセット**します。  
  
## <a name="related-sections"></a>関連項目  
 [ASP.NET Web アプリケーション](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))  
 ASP.NET アプリケーション、Web フォームおよび Web サービスを作成する場合の概要と詳細なステップごとの手順を示します。  
  
 [Windows アプリケーション](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))  
 Windows フォームおよびコンソール アプリケーションの操作に関する詳細情報を提供します。  
  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 について説明します、**データセット**オブジェクトと使用してアプリケーション データを管理する方法。  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 について説明します、 **DataTable**オブジェクトと使用して単独でまたはの一部としてアプリケーション データを管理する方法、**データセット**します。  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
