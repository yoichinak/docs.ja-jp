---
title: ADO.NET の概要
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 7ec3b5f4dd08a39f96ed28e6666fd4b00bced903
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607363"
---
# <a name="adonet-overview"></a>ADO.NET の概要
ADO.NET は、SQL Server や XML などのデータ ソースや、OLE DB や ODBC 経由で公開されるデータ ソースに対する一貫性を持ったアクセス機能を実現します。 データを共有する消費者向けアプリケーションで ADO.NET を使用することで、そのようなデータ ソースへの接続や、データ ソースに格納されているデータの取得、操作、更新を実行できます。  
  
 ADO.NET は、データ操作の中からデータ アクセス機能を分離し、個別にまたは組み合わせて使用できる、独立したコンポーネントへと分解します。 ADO.NET には、データベースとの接続、コマンドの実行、および結果の取得を行うための .NET Framework データ プロバイダーが含まれます。 この結果は直接処理され、ADO.NET <xref:System.Data.DataSet> オブジェクトに格納されます。この結果は、ユーザーに暫定的に公開したり、複数のソースからのデータと組み合わせたり、層間で受け渡したりするために使用されます。 `DataSet` オブジェクトを .NET Framework データ プロバイダーに関係なく使用した場合でも、アプリケーションにとってローカルなデータや XML から提供されたデータを管理できます。  
  
 ADO.NET クラスは System.Data.dll にあり、System.Xml.dll に含まれている XML クラスに統合されています。 データベースに接続するサンプル コードは、そこからデータを取得し、コンソール ウィンドウでそのデータを表示するを参照してください。 [ADO.NET のコード例](../../../../docs/framework/data/adonet/ado-net-code-examples.md)します。  
  
 マネージド コードを作成する開発者は、ADO.NET により、ネイティブのコンポーネント オブジェクト モデル (COM) 開発者が ActiveX Data Object (ADO) によって利用できる機能と同等の機能を利用できます。 .NET アプリケーションでのデータのアクセスには、ADO ではなく ADO.NET を使用することをお勧めします。  
  
 ADO.NET は、.NET Framework におけるデータ アクセスの最も直接的な方法を提供します。 基になるストレージ モデルではなく、概念モデルに対して動作するアプリケーションを使用するより高度な抽象化を参照してください、 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)します。  
  
 **プライバシーに関する声明**:ユーザーの間、System.Data.dll、System.Data.Design.dll、System.Data.OracleClient.dll、System.Data.SqlXml.dll、System.Data.Linq.dll、System.Data.SqlServerCe.dll、system.data.datasetextensions.dll の各およびアセンブリによって区別されません。個人データとそれ以外のデータ。  これらのアセンブリによって、ユーザーの個人データの収集、格納、送信が実行されることはありません。 ただし、サードパーティ製のアプリケーションでこれらのアセンブリが使用され、ユーザーの個人データの収集、格納、送信が行われる可能性はあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ADO.NET のアーキテクチャ](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 ADO.NET のアーキテクチャとコンポーネントの概要を説明します。  
  
 [ADO.NET テクノロジのオプションとガイドライン](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 エンティティ データ プラットフォームに含まれている製品とテクノロジを説明します。  
  
 [LINQ と ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 ADO.NET での統合言語クエリ (LINQ) の実装方法を説明し、関連項目へのリンクを示します。  
  
 [.NET Framework データ プロバイダー](../../../../docs/framework/data/adonet/data-providers.md)  
 .NET Framework データ プロバイダーと、ADO.NET に同梱される .NET Framework データ プロバイダーのデザインの概要を説明します。  
  
 [ADO.NET データセット](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 `DataSet` のデザインとコンポーネントの概要を説明します。  
  
 [ADO.NET での side-by-side 実行](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 ADO.NET のバージョン間の相違と、その相違が side-by-side 実行とアプリケーションの互換性に及ぼす影響について説明します。  
  
 [ADO.NET のコード例](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 ADO.NET データ プロバイダーを使用してデータを取得するコード サンプルです。  
  
## <a name="related-sections"></a>関連項目  
 [ADO.NET の新機能](../../../../docs/framework/data/adonet/whats-new.md)  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] の新機能について説明します。  
  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 ADO.NET を使用する場合の安全なコーディング方法について説明します。  
  
 [ADO.NET でのデータ型のマッピング](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 .NET Framework データ型と .NET Framework データ プロバイダーとの間のデータ型のマッピングについて説明します。  
  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 データ ソースへの接続、データの取得、データの変更の方法について説明します。 これには、`DataReaders` と `DataAdapters` が含まれます。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [Visual Studio でのデータへのアクセス](/visualstudio/data-tools/accessing-data-in-visual-studio)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
