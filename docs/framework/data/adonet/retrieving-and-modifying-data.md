---
title: ADO.NET でのデータの取得および変更
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: a5ac8fbd2a53d2670471c1ef5e59508f582ed944
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881434"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>ADO.NET でのデータの取得および変更
データベース アプリケーションの主な機能は、データ ソースとの接続およびデータベースに格納されているデータの取得です。 使用してデータの取得も同様のコマンドを実行することができます、アプリケーションと、データ ソース間のブリッジとしての ADO.NET の .NET Framework データ プロバイダーの機能、 **DataReader**または**DataAdapter**. データベースに格納されているデータを更新する機能は、データベース アプリケーションの重要な機能の 1 つです。 ADO.NET では、データを更新する必要がありますを使用して、 **DataAdapter**と<xref:System.Data.DataSet>、および**コマンド**オブジェクトも含まれますトランザクションを使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データ ソースへの接続](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 データ ソースへの接続を確立する方法、および接続イベントを使用する方法について説明します。  
  
 [接続文字列](../../../../docs/framework/data/adonet/connection-strings.md)  
 接続文字列のキーワード、セキュリティ情報、セキュリティ情報の格納や取得など、接続文字列を使用するうえでのさまざまな側面について説明します。  
  
 [接続プール](../../../../docs/framework/data/adonet/connection-pooling.md)  
 .NET Framework Data Provider の接続プールについて説明します。  
  
 [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 コマンドおよびコマンド ビルダーを作成する方法、パラメーターを構成する方法、およびコマンドを実行してデータを取得および変更する方法について説明します。  
  
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 DataReaders、DataAdapters、パラメーター、DataAdapter イベントの処理、およびバッチ操作の実行について説明します。  
  
 [トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 ローカル トランザクションや分散トランザクションの実行方法、およびオプティミスティック コンカレンシーの使用方法について説明します。  
  
 [ID 値および Autonumber 値の取得](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 生成された値のマッピングの例を示します、 **identity**用または SQL Server テーブル内の列、 **Autonumber**テーブルでの挿入された行の列に、Microsoft Access テーブルのフィールド。 `DataTable` での ID 値の結合について説明します。  
  
 [バイナリ データの取得](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 バイナリ データまたは使用して大規模なデータ構造体を取得する方法について説明します`CommandBehavior`します。`SequentialAccess` 既定の動作を変更する、`DataReader`します。  
  
 [ストアド プロシージャでのデータの変更](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 ストアド プロシージャの入力パラメーターおよび出力パラメーターを使用してデータベースに行を挿入し、新しい ID 値を返す方法について説明します。  
  
 [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 データベースまたはカタログ、データベース内のテーブルおよびビュー、テーブルに対して存在する制約、およびその他のスキーマ情報をデータ ソースから取得する方法について説明します。  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 プロバイダー ファクトリ モデルについて説明し、`System.Data.Common` 名前空間の基本クラスの使用方法を示します。  
  
 [ADO.NET のデータ追跡](../../../../docs/framework/data/adonet/data-tracing.md)  
 ADO.NET が備える組み込みデータ トレース機能のしくみについて説明します。  
  
 [パフォーマンス カウンター](../../../../docs/framework/data/adonet/performance-counters.md)  
 `SqlClient` および `OracleClient` で使用できるパフォーマンス カウンターについて説明します。  
  
 [非同期の概要](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 非同期プログラミングの ADO.NET のサポートについて説明します。  
  
 [SqlClient ストリーミング サポート](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 完全にメモリに読み込まれていることをしなくても SQL Server からアプリケーション データのストリームを記述する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET でのデータ型のマッピング](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [DataSet、DataTable、および DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET アプリケーションのセキュリティ保護](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server と ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
