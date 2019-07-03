---
title: Entity Framework の用語
ms.date: 03/30/2017
ms.assetid: fa2a1bd1-6118-487b-8673-eebc66b92945
ms.openlocfilehash: bc3712628d308629208af893e8fdee16cbba1e93
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539874"
---
# <a name="entity-framework-terminology"></a>Entity Framework の用語
このトピックで頻繁に参照用語の定義[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]ドキュメント。 追加情報を確認できる関連トピックへのリンクも示しています。  
  
|用語|定義|  
|----------|----------------|  
|関連付け|エンティティ型間のリレーションシップの定義。<br /><br /> 詳細については、次を参照してください。 [Association 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#association-element-csdl)と[アソシエーション型](../../../../../docs/framework/data/adonet/association-type.md)します。|  
|関連付けセット|同じ型のアソシエーションのインスタンスの論理コンテナー。<br /><br /> 詳細については、次を参照してください。 [AssociationSet 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#associationset-element-csdl)と[アソシエーション セット](../../../../../docs/framework/data/adonet/association-set.md)します。|  
|Code First|Entity Framework 4.1 以降では、Code First の開発を使用してモデルをプログラムで作成することもできます。 Code First の開発に対しては、2 つの異なるシナリオがあります。 どちらの場合でも、開発者は .NET Framework のクラス定義をコーディングしてモデルを定義し、データ注釈または Fluent API を使用してオプションで追加のマッピングまたは構成を指定します。<br /><br /> ただし、Code First の開発が含まれている、 [Entity Framework 5.0](https://go.microsoft.com/fwlink/?LinkId=234900)します。 Entity Framework 5.0 は .NET Framework の一部ではありませんが、.NET Framework 4.5 で構成されます。 Entity Framework 5.0 は、 [' Entity Framework'](https://go.microsoft.com/fwlink/?LinkID=215714)[NuGet](https://go.microsoft.com/fwlink/?LinkId=232488)パッケージ。 詳細については、次を参照してください。 [Entity Framework リリースおよびバージョン管理](https://go.microsoft.com/fwlink/?LinkId=234899)します。|  
|コマンド ツリー|すべての共通プログラム表現[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]クエリの 1 つまたは複数の式で構成されます。<br /><br /> 詳細については、次を参照してください。 [Entity Framework の概要](../../../../../docs/framework/data/adonet/ef/overview.md)します。|  
|複合型|概念モデルに定義されている複合プロパティを表す .NET Framework クラス。 複合型により、スカラー プロパティをエンティティ内で整理することができます。 複合オブジェクトは、複合型のインスタンスです。 詳細については、次を参照してください。 [ComplexType 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#complextype-element-csdl)と[複合型](../../../../../docs/framework/data/adonet/complex-type.md)します。|  
|ComplexType|キー プロパティを持たないエンティティ型の非スカラー プロパティを表すデータ型の仕様。<br /><br /> 詳細については、次を参照してください。 [ComplexType 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#complextype-element-csdl)と[複合型](../../../../../docs/framework/data/adonet/complex-type.md)します。|  
|概念モデル|[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] のアプリケーションのドメインにおけるエンティティ型、複合型、アソシエーション、エンティティ コンテナー、エンティティ セット、およびアソシエーション セットの抽象的な仕様。 概念モデルは、CSDL で .csdl ファイルに定義されます。<br /><br /> 詳細については、次を参照してください。[モデリング ファイルとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)します。|  
|.csdl ファイル|CSDL で表現された概念モデルを含む XML ファイル。|  
|概念スキーマ定義言語 (CSDL)|概念モデルのエンティティ型、関連付け、エンティティ コンテナー、エンティティ セット、および関連付けセットを定義するための XML ベースの言語。<br /><br /> 詳細については、「 [CSDL Specification](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)」を参照してください。|  
|コンテナー|エンティティ セットとアソシエーション セットの論理的なグループ。<br /><br /> 詳細については、次を参照してください。 [EntityContainer 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entitycontainer-element-csdl)と[エンティティ コンテナー](../../../../../docs/framework/data/adonet/entity-container.md)します。|  
|コンカレンシー|複数のユーザーが共有データに同時にアクセスや変更を行うことができるようにする処理。 既定では、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、オプティミスティック同時実行制御モデルを実装しています。|  
|方向|一部のアソシエーションの非対称の性質を表します。 方向は、スキーマの `FromRole` 要素または `ToRole` 要素の `NavigationProperty` 属性と `ReferentialConstraint` 属性で指定されます。<br /><br /> 詳細については、次を参照してください。 [NavigationProperty 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#navigationproperty-element-csdl)と[ナビゲーション プロパティ](../../../../../docs/framework/data/adonet/navigation-property.md)します。|  
|一括読み込み|関連オブジェクトの特定のセットを、クエリで明示的に要求されたオブジェクトと共に読み込むプロセス。|  
|.edmx ファイル|概念モデル (CSDL)、ストレージ モデル (SSDL)、および概念モデルとストレージ モデルの間のマッピング (MSL) を含む XML ファイル。 .Edmx ファイルは、Entity Data Model ツールによって作成されます。 詳細については、次を参照してください。 [.edmx ファイルの概要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))します。|  
|end|アソシエーションに参加しているエンティティ。<br /><br /> 詳細については、次を参照してください。 [End 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#end-element-csdl)と[アソシエーション end](../../../../../docs/framework/data/adonet/association-end.md)します。|  
|entity|データ型を定義する際に基づくアプリケーションのドメインにおける概念。<br /><br /> 詳細については、次を参照してください。 [EntityType 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entitytype-element-csdl)と[エンティティ型](../../../../../docs/framework/data/adonet/entity-type.md)します。|  
|EntityClient|ストレージに依存しない ADO.NET データ プロバイダーなどのクラスを含む`EntityConnection`、 `EntityCommand`、および`EntityDataReader`します。 連携[!INCLUDE[esql](../../../../../includes/esql-md.md)]など、ストレージ固有の ADO.NET データ プロバイダーに接続して`SqlClient`します。<br /><br /> 詳細については、次を参照してください。 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)します。|  
|エンティティ コンテナー|指定された名前空間に実装されるエンティティ セットとアソシエーション セットを指定します。<br /><br /> 詳細については、次を参照してください。 [EntityContainer 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entitycontainer-element-csdl)と[エンティティ コンテナー](../../../../../docs/framework/data/adonet/entity-container.md)します。|  
|Entity Data Model (EDM)|格納される形式に関係なく、エンティティおよびリレーションシップとしてデータ構造を記述する一連の概念。<br /><br /> 詳細については、次を参照してください。 [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)します。|  
|Entity Framework|開発者がデータ ソースの論理スキーマにマップされた概念モデルを使用できるようにすることで、データ指向のソフトウェア アプリケーションの開発をサポートするテクノロジ セット。<br /><br /> 詳細については、次を参照してください。 [Entity Framework の概要](../../../../../docs/framework/data/adonet/ef/overview.md)します。|  
|エンティティ セット|指定された型とそのサブタイプのエンティティの論理コンテナー。 エンティティ セットは、データベース内のテーブルにマップされます。<br /><br /> 詳細については、次を参照してください。 [EntitySet 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entityset-element-csdl)と[エンティティ セット](../../../../../docs/framework/data/adonet/entity-set.md)します。|  
|Entity SQL|エンティティの概念スキーマを直接操作し、継承やリレーションシップなどの概念モデルの概念をサポートする、ストレージの影響を受けない SQL の言語。<br /><br /> 詳細については、次を参照してください。 [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)します。|  
|エンティティ型|概念モデルで定義されているエンティティを表す .NET Framework クラスです。 エンティティ型には、スカラー プロパティ、複合プロパティ、およびナビゲーション プロパティが含まれる場合があります。 オブジェクトは、エンティティ型のインスタンスです。 詳細については、次を参照してください。[オブジェクトの操作](../../../../../docs/framework/data/adonet/ef/working-with-objects.md)します。|  
|EntityType|キーやプロパティの名前付きセットを含み、概念モデルまたはストレージ モデルの最上位項目を表すデータ型の仕様。<br /><br /> 詳細については、次を参照してください。 [EntityType 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entitytype-element-csdl)と[エンティティ型](../../../../../docs/framework/data/adonet/entity-type.md)します。|  
|明示的な読み込み|クエリがオブジェクトを返す場合、関連オブジェクトは同時に読み込まれません。 既定では、関連オブジェクトは、ナビゲーション プロパティの `Load` メソッドを使用して明示的に要求されるまで読み込まれません。|  
|外部キーの関連付け (アソシエーション)|外部キー プロパティで管理されるエンティティ間のアソシエーション。|  
|依存リレーションシップ|プリンシパル エンティティの主キーが依存エンティティの主キーの一部であるリレーションシップ。 このようなリレーションシップでは、プリンシパル エンティティが存在しないと、依存エンティティは存在できません。|  
|独立した関連付け (アソシエーション)|独立オブジェクトによって表され、追跡されるエンティティ間のアソシエーション。|  
|key|エンティティ型の一意のインスタンスを識別するために使用されるプロパティまたはプロパティ セットを指定するエンティティ型の属性。 オブジェクト レイヤーでは、<xref:System.Data.EntityKey> クラスで表現されます。<br /><br /> 詳細については、次を参照してください。[キー要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#key-element-csdl)と[エンティティ キー](../../../../../docs/framework/data/adonet/entity-key.md)します。|  
|遅延読み込み|クエリがオブジェクトを返す場合、関連オブジェクトは同時に読み込まれません。 代わりに、ナビゲーション プロパティへのアクセス時に自動的に読み込まれます。|  
|LINQ to Entities|Visual c# および Visual Basic での直接的な宣言型の方法で表現できるに走査、フィルター、およびプロジェクション操作を許可するクエリ演算子のセットを定義するクエリ構文。<br /><br /> 詳細については、次を参照してください。 [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)します。|  
|マップ|概念モデルの項目とストレージ モデルの項目の対応付けの指定。<br /><br /> 詳細については、次を参照してください。 [MSL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/msl-specification.md)します。|  
|.msl ファイル|MSL で表現された概念モデルとストレージ モデルの間のマッピングを含む XML ファイル。|  
|マッピング仕様言語 (MSL)|概念モデルで定義された項目をストレージ モデルの項目に対応付ける XML ベースの言語。<br /><br /> 詳細については、次を参照してください。 [MSL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/msl-specification.md)します。|  
|変更関数|データ ソースでデータを挿入、更新、および削除するために使用されるストアド プロシージャ。 この関数は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で生成されるコマンドの代わりに使用されます。 変更関数は、ストレージ モデルの `Function` 要素で定義されます。 [ModificationFunctionMapping](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716778(v=vs.100))要素が挿入、更新、および概念モデルで定義されているエンティティに対する操作を削除するには、この変更関数をマップします。|  
|多重度|アソシエーションによって定義されているリレーションシップの両側に存在できるエンティティの数。 カーディナリティとも呼ばれます。<br /><br /> 詳細については、次を参照してください。 [End 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#end-element-csdl)と[アソシエーション end](../../../../../docs/framework/data/adonet/association-end.md)します。|  
|Multiple-Entity-Sets-per-Type|1 つのエンティティ型を複数のエンティティ セットで定義できる機能。<br /><br /> 詳細については、次を参照してください。 [EntitySet 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#entityset-element-csdl)と[方法。型ごとに複数のエンティティ セットでモデルを定義](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738537(v=vs.100))します。|  
|ナビゲーション プロパティ|アソシエーションによって定義されている別のエンティティ型とのリレーションシップを表すエンティティ型のプロパティ。 ナビゲーション プロパティは、アソシエーションのもう一方の End での複数要素の接続性に応じて、関連オブジェクトを <xref:System.Data.Objects.DataClasses.EntityCollection%601> または <xref:System.Data.Objects.DataClasses.EntityReference%601> として返すために使用されます。<br /><br /> 詳細については、次を参照してください。 [NavigationProperty 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#navigationproperty-element-csdl)と[ナビゲーション プロパティ](../../../../../docs/framework/data/adonet/navigation-property.md)します。|  
|クエリ パス|オブジェクト クエリの実行時に返す関連オブジェクトを指定するパスの文字列表記。 クエリ パスは、<xref:System.Data.Objects.ObjectQuery%601.Include%2A> に対して <xref:System.Data.Objects.ObjectQuery%601> メソッドを呼び出すことによって定義されます。<br /><br /> 詳細については、次を参照してください。[関連オブジェクトの読み込み](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100))します。|  
|オブジェクト コンテキスト|概念モデルで定義したエンティティ コンテナーを表します。 基になるデータ ソースへの接続を含み、変更の追跡や ID 解決などのサービスを提供します。 オブジェクト コンテキストは、<xref:System.Data.Objects.ObjectContext> クラスまたは `DbContext` クラスのインスタンスで表されます。<br /><br /> `DbContext` 一部である、 [Entity Framework 5.0](https://go.microsoft.com/fwlink/?LinkId=234900)します。 Entity Framework 5.0 は .NET Framework の一部ではありませんが、.NET Framework 4.5 で構成されます。 Entity Framework 5.0 は、 [' Entity Framework'](https://go.microsoft.com/fwlink/?LinkID=215714)[NuGet](https://go.microsoft.com/fwlink/?LinkId=232488)パッケージ。 詳細については、次を参照してください。 [Entity Framework リリースおよびバージョン管理](https://go.microsoft.com/fwlink/?LinkId=234899)します。|  
|オブジェクト レイヤー|Entity Framework によって使用されるエンティティ型およびオブジェクト コンテキストの定義。|  
|オブジェクト クエリ|データをオブジェクトとして返す概念モデルに対してオブジェクト コンテキスト内で実行されるクエリ。<br /><br /> 詳細については、次を参照してください。[オブジェクト クエリ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100))します。|  
|オブジェクト リレーショナル マッピング|リレーショナル データベースのデータをオブジェクト指向のソフトウェア アプリケーションで使用できるデータ型に変換する手法。<br /><br /> [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、ストレージ モデルで定義されたリレーショナル データを概念モデルで定義されたデータ型にマップして、オブジェクト リレーショナル マッピング サービスを提供します。<br /><br /> 詳細については、次を参照してください。[モデリング ファイルとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)します。|  
|オブジェクト サービス|によって提供されるサービス、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] .NET Framework オブジェクトなどのエンティティを操作するアプリケーション コードを有効にします。|  
|永続化非依存オブジェクト|データ ストレージに関連するロジックが含まれていないオブジェクト。 POCO エンティティとも呼ばれます。|  
|POCO|Plain Old CLR Object の略。 別のクラスから継承しないオブジェクト、またはインターフェイスを実装しないオブジェクト。|  
|POCO エンティティ|[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の、<xref:System.Data.Objects.DataClasses.EntityObject> または <xref:System.Data.Objects.DataClasses.ComplexObject> から継承しないエンティティ、または [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] インターフェイスを実装しないエンティティ。 多くの場合、POCO エンティティは既存のドメイン オブジェクトで使用する、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アプリケーション。 このようなエンティティは、永続化非依存性をサポートしています。 詳細については、次を参照してください。 [POCO エンティティの操作](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100))します。|  
|プロキシ オブジェクト|POCO クラスから派生し、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] によって生成されたオブジェクト。変更追跡と遅延読み込みをサポートするために使用されます。 詳細については、次を参照してください。 [POCO プロキシを作成するための要件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd468057(v=vs.100))します。|  
|参照制約|エンティティが他のエンティティと依存関係にあることを示す、概念モデルで定義された制約。 この制約は、依存エンティティのインスタンスが対応する主要エンティティのインスタンスなしでは存在できないことを意味します。<br /><br /> 詳細については、次を参照してください。 [ReferentialConstraint 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#referentialconstraint-element-csdl)と[参照整合性制約](../../../../../docs/framework/data/adonet/referential-integrity-constraint.md)します。|  
|リレーションシップ|エンティティ間の論理的な関係。|  
|ロール|リレーションシップのセマンティクスを明確にするためにアソシエーションの両方の `End` に付けられた名前。<br /><br /> 詳細については、次を参照してください。 [End 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#end-element-csdl)と[アソシエーション end](../../../../../docs/framework/data/adonet/association-end.md)します。|  
|スカラー プロパティ|ストレージ モデルの単一のフィールドにマップされるエンティティのプロパティ。|  
|自己追跡エンティティ|スカラー プロパティ、複合プロパティ、およびナビゲーション プロパティの変更を報告できる、テキスト テンプレート変換ツールキット (T4) から構築されるエンティティ。|  
|単純型|概念モデルでプロパティを定義するために使用されるプリミティブ型。<br /><br /> 詳細については、次を参照してください[概念モデルの型 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)と[Entity Data Model:。プリミティブ データ型](../../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)します。|  
|分割されたエンティティ|ストレージ モデルの 2 つの別個の型にマップされる 1 つのエンティティ型。<br /><br /> 詳細については、「[方法 :2 つのテーブルにマップされている 1 つのエンティティでモデルを定義](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896233(v=vs.100))します。|  
|ストレージ モデル|リレーショナル データベースなど、サポートされているデータ ソースのデータの論理モデルの定義。 ストレージ モデルは、SSDL で .ssdl ファイルに定義されます。<br /><br /> 詳細については、次を参照してください。[モデリング ファイルとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)と[SSDL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/ssdl-specification.md)します。|  
|.ssdl ファイル|SSDL で表現されたストレージ モデルを含む XML ファイル。|  
|ストア スキーマ定義言語 (SSDL)|一般的にデータベース スキーマに対応するストレージ モデルのエンティティ型、アソシエーション、エンティティ コンテナー、エンティティ セット、およびアソシエーション セットの定義に使用される XML ベースの言語。<br /><br /> 詳細については、次を参照してください。 [SSDL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/ssdl-specification.md)します。|  
|table-per-hierarchy|あらゆる型の属性を 1 つのテーブル内の階層構造に含める、データベースにおける型階層のモデリング手法。|  
|table-per-type|一対一リレーションシップを持った複数のテーブルを使用して各種の型をモデリングする、データベースにおける型階層のモデリング手法。|  
  
## <a name="see-also"></a>関連項目

- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
- [Entity Framework の概要](../../../../../docs/framework/data/adonet/ef/overview.md)
- [はじめに](../../../../../docs/framework/data/adonet/ef/getting-started.md)
- [Entity Framework のリソース](../../../../../docs/framework/data/adonet/ef/resources.md)
