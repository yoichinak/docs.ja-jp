---
title: Entity Framework の概要
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 498d0478dc94048a69c393151d3ff8a752706e1c
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539474"
---
# <a name="entity-framework-overview"></a>Entity Framework の概要

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、データ指向のソフトウェア アプリケーション開発をサポートする ADO.NET のテクノロジ セットです。 データ指向のアプリケーションの設計者と開発者はこれまで、2 つの大きく異なる目的を達成するために苦労してきました。 解決すべきビジネス上の問題のエンティティ、リレーションシップ、およびロジックをモデル化する一方で、データの格納と取得に使用するデータ エンジンに取り組む必要もあるからです。 データは複数のストレージ システムにまたがる場合があり、それぞれに独自のプロトコルが存在します。単一のストレージ システムを使用するアプリケーションであっても、ストレージ システムの要件と効率的で保守しやすいアプリケーション コードの記述要件のバランスを取る必要があります。

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用することで、開発者は、顧客や顧客の住所など、ドメイン固有のオブジェクトおよびプロパティの形式でデータを扱うことができます。そのデータが格納されている、基になるデータベース テーブルや列を意識する必要はありません。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用すると、開発者はデータを操作するときに高い抽象化レベルで作業ができ、従来のアプリケーションよりコードの少ないデータ指向アプリケーションの作成と保守が可能になります。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 、.NET Framework のコンポーネントである[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アプリケーションが .NET Framework version 3.5 SP1 以降がインストールされている任意のコンピューターで実行できます。

## <a name="give-life-to-models"></a>モデルへの有効期間を付与します。
 アプリケーションやサービスを構築するとき、従来からの一般的な設計アプローチは、アプリケーションまたはサービスをドメイン モデル、論理モデル、および物理モデルの 3 つの部分に分割する方法です。 ドメイン モデルでは、モデル化の対象となるシステムに存在するエンティティとリレーションシップを定義します。 リレーショナル データベースの論理モデルでは、外部キー制約を用いながらエンティティおよびリレーションシップをテーブルとして正規化します。 物理モデルでは、パーティション分割やインデックス化などのストレージ情報を指定することで、特定のデータ エンジンの機能に対応します。

 物理モデルは、パフォーマンスを向上させるためにデータベース管理者が調整しますが、アプリケーション コードを記述するプログラマは、主に SQL クエリを記述したりストアド プロシージャを呼び出したりすることによって論理モデルを扱うことに専念します。 ドメイン モデルは通常、アプリケーションの要件を収集して伝達するためのツールとして使用されます。プロジェクトの初期段階でのみ表示および検討され、その後ほとんど使用されないのが一般的です。 概念モデルの作成を省略し、実際にリレーショナル データベースのテーブル、列、およびキーを指定することから開始する開発チームも多く存在します。

 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]開発者は、ドメイン モデルのクエリのエンティティとリレーションシップを有効にするとモデルの活用をされます (と呼ばれる、*概念*モデル、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) に依存しながら、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]ものに変換するには操作をデータ ソース固有のコマンド。 これにより、特定のデータ ソースへの依存関係をアプリケーションにハードコーディングしなくても済みます。

 Code First を使用すると、概念モデルはコードのストレージ モデルにマッピングされます。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、オブジェクトの種類と定義する追加の構成に基づいて概念モデルを推論できます。 マッピング メタデータは、ドメインの種類を定義した方法とコードで指定する追加の構成情報の組み合わせに基づいて実行時に生成されます。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、メタデータに基づいて必要に応じてデータベースを生成します。 詳細については、次を参照してください。[概念モデルのマッピングの作成と](https://go.microsoft.com/fwlink/?LinkID=235382)します。

 Entity Data Model ツールでの作業時には、概念モデル、ストレージ モデル、およびこの 2 者間のマッピングは、XML ベースのスキーマで表され、名前の拡張子が同じファイルで定義されます。

- 概念モデルは概念スキーマ定義言語 (CSDL) で定義されます。 CSDL は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]の実装、 [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)します。 ファイル拡張子は .csdl です。

- ストア スキーマ定義言語ファイル (SSDL) はストレージ モデル (論理モデルとも呼ばれる) を定義します。 ファイル拡張子は .ssdl です。

- マッピング仕様言語ファイル (MSL) はストレージ モデルと概念モデルの間のマッピングを定義します。 ファイル拡張子は .msl です。

ストレージ モデルとマッピングは、概念モデル、データ クラス、またはアプリケーション コードを変更することなく、必要に応じて変更できます。 ストレージ モデルはプロバイダー固有なので、データ ソースの違いを意識することなく一貫した概念モデルを扱うことができます。

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]はこれらをモデルとマッピング ファイルを作成するには、読み取り、更新、およびデータ ソース内の同等の操作を概念モデルのエンティティとリレーションシップに対する操作を削除します。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]でも、データ ソース内のストアド プロシージャを概念モデルのエンティティのマッピングがサポートされます。 詳細については、次を参照してください。 [CSDL、SSDL、および MSL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)します。

## <a name="map-objects-to-data"></a>データへのマップ オブジェクト
 オブジェクト指向プログラミングには、データ ストレージ システムと対話するという難題があります。 クラスの編成はリレーショナル データベース テーブルの編成に似ている場合がありますが、完全に一致するわけではありません。 正規化された複数のテーブルと単一のクラスが対応する場合も多く、クラス間のリレーションシップとテーブル間のリレーションシップとで表現方法が異なる場合もあります。 たとえば、販売注文の顧客を表すために、`Order` クラスは `Customer` クラスのインスタンスへの参照が含まれているプロパティを使用する一方で、データベースの `Order` テーブル行には `Customer` テーブルの主キー値に対応する値がある外部キー列 (または列セット) が含まれている場合があります。 `Customer` クラスには `Orders` クラスのインスタンスのコレクションが含まれている `Order` という名前のプロパティがありますが、データベースの `Customer` テーブルに同等の列がない場合などです。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、この方法でリレーションシップを表すか、データベースで表されるリレーションシップに似せるかの柔軟性を開発者に与えます。

 既存のソリューションでは、"インピーダンスのミスマッチ" とよく呼ばれるこの差異を、オブジェクト指向のクラスやプロパティをリレーショナル テーブルやリレーショナル列にマップするだけで埋めようとしてきました。 この従来のアプローチではなく、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]リレーショナル テーブル、列、および論理モデルに外部キー制約を概念モデルのエンティティとリレーションシップにマップします。 これにより、さらに柔軟にオブジェクトを定義して論理モデルを最適化することが可能になります。 Entity Data Model ツールでは、概念モデルに基づく拡張可能なデータ クラスを生成します。 このクラスは、開発者が追加するメンバーで拡張できる部分クラスです。 既定では、特定の概念モデルに対して生成されるクラスは、エンティティをオブジェクトとして具体化したり変更を追跡したり保存したりするサービスを提供する基本クラスから派生します。 開発者はこのようなクラスを使用して、エンティティとリレーションシップを、アソシエーションによって関連付けられたオブジェクトとして操作できます。 また、開発者は、概念モデルに生成されるクラスをカスタマイズすることもできます。 詳細については、次を参照してください。[オブジェクトの操作](../../../../../docs/framework/data/adonet/ef/working-with-objects.md)します。

## <a name="access-and-change-entity-data"></a>エンティティ データにアクセスして変更

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は単なるオブジェクト リレーショナル マッピング ソリューションではなく、基本的には、概念モデルのエンティティとリレーションシップとして表されるデータにアプリケーションからアクセスして変更できるようにするためのものです。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] はモデル ファイルとマッピング ファイルの情報を使用して、概念モデルで表されるエンティティ型に対するオブジェクト クエリをデータ ソース固有のクエリに変換します。 クエリの結果がオブジェクトに具体化される[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]を管理します。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]を概念モデルのクエリを実行し、オブジェクトを返す、次の方法を提供します。

- LINQ to Entities。 概念モデルで定義されているエンティティ型を照会するためには、統合言語クエリ (LINQ) のサポートを提供します。 詳細については、次を参照してください。 [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)します。

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]。 概念モデルのエンティティを直接操作し、Entity Data Model の概念をサポートする SQL のストレージに依存しない言語。 [!INCLUDE[esql](../../../../../includes/esql-md.md)] オブジェクト クエリと EntityClient プロバイダーを使用して実行されるクエリの両方で使用されます。 詳細については、次を参照してください。 [Entity SQL の概要](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)します。

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] には、EntityClient データ プロバイダーが含まれています。 このプロバイダーは接続を管理し、エンティティ クエリをデータ ソース固有のクエリに変換し、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] がエンティティ データをオブジェクトに具体化するために使用するデータ リーダーを返します。 オブジェクトの具体化が不要であれば、アプリケーションで [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行して返された読み取り専用のデータ リーダーを使用できるようにすることで、EntityClient プロバイダーを標準の ADO.NET データ プロバイダーと同様に使用することもできます。 詳細については、次を参照してください。 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)します。

次の図は、データにアクセスするための [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] アーキテクチャを示しています。

![Entity Framework のアーキテクチャ図](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd_EFArchDiagram")

Entity Data Model ツールから派生したクラスを生成できます`System.Data.Objects.ObjectContext`または`System.Data.Entity.DbContext`概念モデルのエンティティ コンテナーを表します。 このオブジェクト コンテキストは、変更の追跡や ID、同時実行、およびリレーションシップの管理などの機能を提供します。 また、このクラスは、データ ソースに挿入、更新、および削除を書き込む `SaveChanges` メソッドも公開します。 このような変更は、クエリと同様に、システムによって自動的に生成されるコマンドで行うことも、特定のストアド プロシージャを使用するように指定することもできます。

## <a name="data-providers"></a>データ プロバイダー

`EntityClient`プロバイダーは、概念エンティティおよびリレーションシップの観点からデータにアクセスして、ADO.NET プロバイダー モデルを拡張します。 [!INCLUDE[esql](../../../../../includes/esql-md.md)] を使用するクエリを実行します。 [!INCLUDE[esql](../../../../../includes/esql-md.md)] は、`EntityClient` がデータベースと通信する基盤となるクエリ言語を提供します。 詳細については、次を参照してください。 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)します。

更新された [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の SqlClient Data Provider は、正規コマンド ツリーをサポートしています。 詳細については、次を参照してください。 [Entity Framework 用 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)します。

## <a name="entity-data-model-tools"></a>Entity data model ツール

組み合わせて、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]ランタイム、Visual Studio では、マッピング ツールとモデリング ツールが含まれています。 詳細については、次を参照してください。[モデリング ファイルとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)します。

## <a name="learn-more"></a>詳細情報

詳細について、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]を参照してください。

[Getting Started](../../../../../docs/framework/data/adonet/ef/getting-started.md) - 取得する方法について説明し、使用して迅速に実行されている、[クイック スタート](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))、単純なを作成する方法を示す[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アプリケーション。

[Entity Framework の用語](../../../../../docs/framework/data/adonet/ef/terminology.md)-エンティティ データ モデルが導入されている用語を多数定義していますと[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]で使用されていると[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]ドキュメント。

[Entity Framework のリソース](../../../../../docs/framework/data/adonet/ef/resources.md)概念説明のトピックへのリンクを提供し、外部トピックおよび構築するためのリソースへのリンク -[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アプリケーション。

## <a name="see-also"></a>関連項目

- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
