---
title: ADO.NET データセット
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: 50e8e8f5e4b3ee2f5a41cb9dad11b5e701135d9e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190939"
---
# <a name="adonet-datasets"></a>ADO.NET データセット
<xref:System.Data.DataSet> オブジェクトは、[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] で非接続型分散データ シナリオをサポートするうえで中心的な役割を果たします。 **データセット**データ ソースに関係なく一貫したリレーショナル プログラミング モデルを提供するデータのメモリ常駐型の表現です。 複数の異なるデータ ソースや XML データと組み合わせて使用でき、アプリケーションにとってローカルなデータの管理にも使用できます。 **データセット**関連テーブル、制約、およびテーブル間のリレーションシップを含む、データの完全なセットを表します。 次の図は、**データセット**オブジェクト モデルです。  
  
 ![ADO.Net グラフィック](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
DataSet オブジェクト モデル  
  
 メソッドと内のオブジェクトを**データセット**リレーショナル データベースのモデルと一致します。  
  
 **データセット**も永続化および XML としてその内容とそのスキーマを XML スキーマ定義言語 (XSD) スキーマとしてを再読み込みできます。 詳しくは、「[DataSet での XML の使用](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)」を参照してください。  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **データセット**によって表現される 0 個以上のテーブルのコレクションを含む<xref:System.Data.DataTable>オブジェクト。 <xref:System.Data.DataTableCollection>すべてが含まれています、 **DataTable**内のオブジェクトを**データセット**します。  
  
 A **DataTable**で定義されている、<xref:System.Data>名前空間、メモリ常駐データの 1 つのテーブルを表します。 このテーブルには、共にテーブルのスキーマを定義する <xref:System.Data.DataColumnCollection> で表現される列と <xref:System.Data.ConstraintCollection> で表現される制約のコレクションが含まれます。 A **DataTable**もによって表される行のコレクションを含む、<xref:System.Data.DataRowCollection>テーブルにデータを格納します。 <xref:System.Data.DataRow> には、行に格納された値の変更を識別できるように、行の現在の状態と共に、行の現在のバージョンと元のバージョンの両方が保持されます。  
  
## <a name="the-dataview-class"></a>DataView クラス  
 <xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータのさまざまなビューを作成できます。この機能は、データ連結アプリケーションで頻繁に使用されます。 <xref:System.Data.DataView> を使用すると、テーブルのデータをさまざまな並べ替え順序で公開したり、行の状態やフィルター式に基づいてデータをフィルター処理したりできます。 詳細については、次を参照してください。 [Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)します。  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A**データセット**でリレーションシップが含まれますその<xref:System.Data.DataRelationCollection>オブジェクト。 表される、リレーションシップ、<xref:System.Data.DataRelation>オブジェクト、1 つの行に関連付けます**DataTable**の行を別**DataTable**します。 リレーションシップは、リレーショナル データベースの主キー列と外部キー列の間に存在する結合パスに似ています。 A **DataRelation**の 2 つのテーブルで一致する列を識別、**データセット**します。  
  
 リレーションシップは、1 つのテーブル内の別のナビゲーションを有効にする、**データセット**します。 重要な要素を**DataRelation**はリレーションシップの名前、関連するもの、テーブルの名前および関連する列の各テーブルにします。 <xref:System.Data.DataColumn> オブジェクトの配列をキー列として指定することによって、テーブルごとに複数の列を使用してリレーションシップを構築できます。 リレーションシップを追加すると、 <xref:System.Data.DataRelationCollection>、必要に応じて追加することができます、 **UniqueKeyConstraint**と**ForeignKeyConstraint**関連する列が変更されたときに、整合性制約を適用するには値。  
  
 詳細については、次を参照してください。 [Datarelation の追加](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)します。  
  
## <a name="xml"></a>XML  
 入力することができます、**データセット**から、XML ストリームまたはドキュメント。 提供する XML ストリームまたはドキュメントを使用することができます、**データセット**データ、スキーマ情報、またはその両方です。 既存のデータまたはスキーマ情報に既に存在すると、XML ストリームまたはドキュメントから提供される情報を組み合わせることができます、**データセット**します。 詳しくは、「[DataSet での XML の使用](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)」を参照してください。  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **データセット**、 **DataTable**、および**DataColumn**がすべて、 **ExtendedProperties**プロパティ。 **ExtendedProperties**は、 **PropertyCollection**結果セットの生成に使用された SELECT ステートメントやデータが生成された時刻などのカスタム情報を配置することができます。 **ExtendedProperties**コレクションのスキーマ情報に保存されて、**データセット**します。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] データセットに格納されている非接続型データを言語統合クエリ機能を提供します。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 標準を使用して[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]構文と、Visual Studio IDE を使用しているときに、コンパイル時の構文チェック、静的な型指定、および IntelliSense のサポートを提供します。  
  
 詳細については、「[LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [DataSet、DataTable、および DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
