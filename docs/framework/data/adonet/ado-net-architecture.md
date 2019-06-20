---
title: ADO.NET のアーキテクチャ
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 282f18cc7d379dffc410a0c62dc3b3e66e0a44f6
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267973"
---
# <a name="adonet-architecture"></a>ADO.NET のアーキテクチャ
従来のデータ処理は、主に接続をベースとした 2 層モデルに基づいていました。 近年、データ処理では多層アーキテクチャの採用が増えてきており、アプリケーションのスケーラビリティを高める非接続型アプローチが主流になりつつあります。  
  
## <a name="adonet-components"></a>ADO.NET のコンポーネント  
 ADO.NET にアクセスしてデータを操作するための 2 つの主要なコンポーネントは、.NET Framework データ プロバイダーと<xref:System.Data.DataSet>します。  
  
### <a name="net-framework-data-providers"></a>.NET Framework データ プロバイダー  
 .NET Framework データ プロバイダーは、データの操作と、データに対する高速かつ前方参照専用、読み込み専用のアクセスを実行することを明確な目標としてデザインされたコンポーネントです。 `Connection` オブジェクトはデータ ソースへの接続を実現します。 `Command` オブジェクトによりデータベース コマンドにアクセスし、データの取得、データの修正、ストアド プロシージャの実行、およびパラメーター情報の送信または取得を実行できます。 `DataReader` は、データ ソースからのパフォーマンスの高いデータ ストリームを実現します。 最後に、`DataAdapter` は `DataSet` オブジェクトとデータ ソース間のブリッジとして機能します。 `DataAdapter` では `Command` オブジェクトを使用してデータ ソースに対して SQL コマンドを実行して、`DataSet` にデータを読み込むと同時に、`DataSet` のデータに加えられた変更をデータ ソースと調整します。 詳細については、次を参照してください。 [.NET Framework データ プロバイダー](../../../../docs/framework/data/adonet/data-providers.md)と[ADO.NET での変更データの取得および](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)します。  
  
### <a name="the-dataset"></a>DataSet  
 ADO.NET `DataSet` は、どのデータ ソースにも依存しないデータ アクセスを行うことを目的としています。 したがって、複数の異なるデータ ソースと併用したり、XML データと併用したり、アプリケーションにとってローカルなデータを管理するために使用したりできます。 `DataSet` には、1 つ以上の <xref:System.Data.DataTable> オブジェクトのコレクションが含まれます。このオブジェクトは、データの行と列に加え、主キー、外部キー、制約、および `DataTable` オブジェクトのリレーション情報で構成されます。 詳細については、次を参照してください。 [Dataset、Datatable、および Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)します。  
  
 次の図は、.NET Framework データ プロバイダー間のリレーションシップと`DataSet`します。  
  
 ![ADO.Net グラフィック](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
ADO.NET のアーキテクチャ  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>DataReader または DataSet の選択  
 アプリケーションが使用する必要があるかどうかを決定する際に、 `DataReader` (を参照してください[DataReader によるデータの取得](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) または`DataSet`(を参照してください[Dataset、Datatable、および Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)) の種類を検討してください。アプリケーションに必要な機能です。 以下を実行する場合は `DataSet` を使用します。  
  
- アプリケーションでデータをローカルにキャッシュすると、そのデータを操作できます。 クエリの実行結果を読み取るだけで良い場合は、`DataReader` の使用をお勧めします。  
  
- 層間で、または XML Web サービスからデータをリモート処理する場合。  
  
- Windows フォーム コントロールとの連結、または複数ソースに属するデータの組み合わせや関連付けなど、データと動的に対話する場合。  
  
- データ ソースとの接続を開かずにデータに対する広範な処理を実行する場合。他のクライアントが使用できるように、接続が解放されます。  
  
 `DataSet` の機能が必要ない場合は、`DataReader` を使用して前方参照専用、読み取り専用の方法でデータを返すことにより、アプリケーションのパフォーマンスを向上させることができます。 ですが、`DataAdapter`を使用して、`DataReader`の内容を格納する、 `DataSet` (を参照してください[DataAdapter からの Dataset](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)) を使用して、`DataReader`メモリを保存するため、パフォーマンスを向上させることができますによって使用される、`DataSet`を作成しの内容を格納するために必要な処理を回避し、`DataSet`します。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 LINQ to DataSet はクエリ機能を備え、DataSet オブジェクトでキャッシュされたデータに対するコンパイル時の型チェックを行います。 これを使用すると、C# や Visual Basic などのいずれかの .NET Framework 開発言語でクエリを記述できます。 詳細については、「[LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 LINQ to SQL では、リレーショナル データベースのデータ構造と対応付けられたオブジェクト モデルに対し、中間概念モデルを使用することなくクエリを実行できます。 それぞれのテーブルは独立したクラスで表現され、オブジェクト モデルとリレーショナル データベース スキーマとが緊密に結び付けられます。 LINQ to SQL では、オブジェクト モデルの統合言語クエリが Transact-SQL に変換され、データベースに送信されて実行されます。 データベースから結果が返されると、LINQ to SQL によって、その結果が再びオブジェクトへと変換されます。 詳細については、「[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)」を参照してください。  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework は、開発者がリレーショナル ストレージ スキーマに対して直接プログラムを作成するのではなく、概念アプリケーション モデルに対してプログラムを作成して、データ アクセス アプリケーションを作成できるように設計されています。 その目的は、データ指向アプリケーションに必要なコードの量と保守作業の量を減らすことです。 詳細については、次を参照してください。 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)します。  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、Web またはイントラネットにデータ サービスを展開するために使用されます。 データは、エンティティ データ モデルの仕様に従ってエンティティおよびリレーションシップとして構成されます。 このモデルで展開されるデータは、標準 HTTP プロトコルによってアドレス指定可能です。 詳細については、「[WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)」を参照してください。  
  
## <a name="xml-and-adonet"></a>XML と ADO.NET  
 ADO.NET では、データに対する非接続型アクセスを提供する XML の機能を活用します。 ADO.NET がデザインされた手の形で - と密接に連携、.NET Framework の XML クラス両方は、1 つのアーキテクチャのコンポーネントです。  
  
 ADO.NET および .NET Framework の XML クラスに集約されて、`DataSet`オブジェクト。 `DataSet` に、XML ソース (ファイルまたは XML ストリーム) に含まれるデータを入力できます。 `DataSet` は、XML スキーマ定義言語 (XSD) スキーマを含む、W3C (World Wide Web Consortium) 準拠の XML として作成できます。これには `DataSet` 内のデータのソースは関係ありません。 `DataSet` のネイティブのシリアル化形式は XML であることから、層間でデータを移動するための媒体として優れており、XML Web サービスとの間でデータとスキーマ コンテキストをリモート処理する場合には `DataSet` が最適な選択となります。 詳細については、「[XML ドキュメントと XML データ](../../../../docs/standard/data/xml/index.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
