---
title: F# を使用した Azure Table Storage の概要
description: Azure Table storage または Azure Cosmos DB を使用してクラウドで構造化データを格納します。
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 54c777acd454e4f675175b814675c185e41ad9a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756352"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Azure Table storage と F を使用した Azure Cosmos DB Table API の概要します。\#

Azure Table storage とは、クラウドで構造化 NoSQL データを格納するサービスです。 テーブル ストレージは、スキーマレス設計のキー/属性ストアです。 Table storage は、スキーマなしであるために、簡単に、アプリケーションの進化のニーズに合わせてデータを調整できますが。 データへのアクセスとは、高速でコスト効率に優れたアプリケーションのすべての種類です。 テーブル ストレージは、大幅に従来の SQL と同様、大量のデータよりも低コストでは通常です。

Table storage を使用して、web アプリケーション、アドレス帳、デバイスについては、その他の種類のサービスに必要なメタデータ用のユーザー データなどの柔軟なデータセットを格納することができます。 テーブルのエンティティの任意の数を格納して、ストレージ アカウントは、ストレージ アカウントの容量の上限に達するまで、テーブルの任意の数を含めることができます。

Azure Cosmos DB では、Azure Table storage に書き込まれなどのプレミアム機能を必要とするアプリケーションを Table API を提供します。

- ターンキー グローバル配信。
- 世界中の専用スループット。
- 99 パーセン タイルで 1 桁ミリ秒の待機時間。
- 高可用性を保証します。
- 自動セカンダリ インデックス作成。

Azure Table storage 用に記述されたアプリケーションでは、コードの変更を Table API を使用して、Azure Cosmos DB に移行でき、高度な機能を利用することができます。 Table API では、.NET、Java、Python、および Node.js の使用可能なクライアント Sdk があります。

詳細については、次を参照してください。 [Azure Cosmos DB Table API の概要](https://docs.microsoft.com/azure/cosmos-db/table-introduction)します。

## <a name="about-this-tutorial"></a>このチュートリアルについて

このチュートリアルでは、Azure Table storage またはなど、Azure Cosmos DB テーブル API、作成しテーブルの削除し挿入、更新、削除、およびテーブル データのクエリを使用していくつかの一般的なタスクを実行する F# コードを記述する方法を示します。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するのにはまず[Azure ストレージ アカウントを作成](/azure/storage/storage-create-storage-account)または[Azure Cosmos DB アカウント](https://azure.microsoft.com/try/cosmosdb/)します。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成して、F# スクリプトと開始 F# 対話型

この記事のサンプルは、F# アプリケーションまたは F# スクリプトのいずれかで使用できます。 F# スクリプトを作成するには、ファイルを作成、`.fsx`拡張機能の例では、 `tables.fsx`、F# 開発環境にします。

次に、使用、[パッケージ マネージャー](package-management.md)など[パケット](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブ。 用にもう一度やって`Microsoft.WindowsAzure.ConfigurationManager`Microsoft.Azure 名前空間を取得するためにします。

### <a name="add-namespace-declarations"></a>名前空間宣言を追加します。

次の追加`open`ステートメントの先頭に、`tables.fsx`ファイル。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Azure Storage 接続文字列を取得します。

Azure Storage Table service に接続する場合は、このチュートリアルでは、接続文字列を必要があります。 Azure portal から接続文字列をコピーすることができます。 接続文字列の詳細については、次を参照してください。[ストレージ接続文字列を構成](/azure/storage/storage-configure-connection-string)します。

### <a name="get-your-azure-cosmos-db-connection-string"></a>Azure Cosmos DB 接続文字列を取得します。

Azure Cosmos DB に接続する場合は、このチュートリアルでは、接続文字列を必要があります。 Azure portal から接続文字列をコピーすることができます。 Cosmos DB アカウントに、Azure portal に移動**設定** > **接続文字列**、 をクリックし、**コピー**プライマリ接続をコピーする ボタン文字列。 

このチュートリアルでは、次の例のように、スクリプトで、接続文字列を入力します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

ただし、これは**しないで**の実際のプロジェクト。 ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。 常に、ストレージ アカウント キーを保護するように注意します。 ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存することは、他のユーザーに配布しないでください。 侵害されていると思われる場合は、Azure Portal を使用して、キーを再生成することができます。

実際のアプリケーションは、ストレージ接続文字列を維持するために最善の方法は、構成ファイルです。 構成ファイルから接続文字列を取得するには、は、これを行うことができます。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Azure Configuration Manager の使用は省略可能です。 .NET Framework のなどの API を使用することもできます。`ConfigurationManager`型。

### <a name="parse-the-connection-string"></a>接続文字列を解析します。

接続文字列を解析するには、次のように使用します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

これにより返されます、`CloudStorageAccount`します。

### <a name="create-the-table-service-client"></a>Table service クライアントを作成します。

`CloudTableClient`クラスでは、テーブルとテーブル ストレージ内のエンティティを取得することができます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

データを読み取るし、Table storage にデータを書き込むコードを記述する準備が整いました。

### <a name="create-a-table"></a>テーブルの作成

この例では、存在しない場合は、テーブルを作成する方法を示します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>エンティティをテーブルに追加します。

継承する型を持つエンティティがある`TableEntity`します。 拡張する`TableEntity`、好きなように、型*する必要があります*パラメーターなしのコンス トラクターします。 両方があるプロパティのみ`get`と`set`Azure テーブルに格納されます。

エンティティのパーティション キーと行キーは、テーブル内のエンティティを一意に識別します。 同じパーティション キーを持つエンティティは、別のパーティション キーを持つよりも迅速に照会できますが、並列操作のスケーラビリティが向上により、多様なパーティション キーを使用します。

次の例に示します、`Customer`を使用して、`lastName`パーティション キーとして、`firstName`行キーとして。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

ここで追加`Customer`テーブルにします。 これを行うには、作成、`TableOperation`テーブルでを実行します。 この場合、作成、`Insert`操作。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>エンティティのバッチを挿入します。

エンティティのバッチは、1 回の書き込み操作を使用してテーブルに挿入できます。 バッチ操作は、操作を 1 回の実行にまとめることができますが、いくつかの制限。

- 更新プログラムを実行する削除、および同じバッチ操作に挿入します。
- バッチ操作では、最大 100 個のエンティティを含めることができます。
- すべてのエンティティをバッチ操作で同じパーティション キーが必要です。
- バッチ操作でクエリを実行することはできますが、バッチ内の唯一の操作があります。

2 つの挿入をバッチ操作に結合したいくつかのコードを次に示します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>パーティション内のすべてのエンティティを取得します。

テーブルに対してパーティション内のすべてのエンティティを照会するを使用して、`TableQuery`オブジェクト。 ここでは、フィルター処理するエンティティをパーティション キーは、"Smith"。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

結果を印刷するようになりました。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>パーティション内のエンティティの範囲を取得します。

パーティション内のすべてのエンティティのクエリを実行しない場合は、パーティション キー フィルターと行キー フィルターを組み合わせることで、範囲を指定できます。 ここでは、フィルターを使用する 2 つ、"Smith"パーティション内のすべてのエンティティを取得するのに、行キー (名) 文字から始まり、アルファベットの"M"よりも前。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

結果を印刷するようになりました。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>1 つのエンティティを取得します。

1 つの特定のエンティティを取得するクエリを記述することができます。 ここを使用する、 `TableOperation` "Ben Smith"というユーザーを指定します。 コレクションではなく、得られる、`Customer`します。 Table service から単一のエンティティを取得する最も簡単な方法は、クエリでパーティション キーと行キーの両方を指定します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

結果を印刷するようになりました。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>エンティティを置換します。

エンティティを更新するには、テーブル サービスから取得し、エンティティ オブジェクトを変更および変更を保存して、サービスを使用してテーブルに、`Replace`操作。 これにより、操作に失敗する場合、取得した後、サーバー上のエンティティを変更しない限り、サーバーが完全に置換するエンティティ。 このエラーは、アプリケーションが他のソースからの変更を誤って上書きを防止します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>エンティティを挿入または置換

場合によっては、テーブルにエンティティが存在するかどうかがわからない。 それに格納されている現在の値が不要になった場合は、します。 使用することができます`InsertOrReplace`に、エンティティを作成するか、その状態に関係なく、ユーザーが存在する場合に置き換えます。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>エンティティのプロパティのサブセットを照会します。

テーブル クエリでは、それらのすべてではなく、エンティティからプロパティをいくつかを取得できます。 この手法は、プロジェクションと呼ばれるには、特に大規模なエンティティの場合のクエリ パフォーマンスを向上できます。 ここを使用して電子メールにのみのアドレスを返す`DynamicTableEntity`と`EntityResolver`します。 Table service でアカウントを使用している場合にのみ、このコードが実行されるように、プロジェクションは、ローカル ストレージ エミュレーターでサポートされないことに注意してください。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>ページ内のエンティティを非同期的に取得します。

多数のエンティティを読み取るし、それらすべてで返されるを待機しているのではなく、取得されるようにそれらを処理する場合は、セグメント化されたクエリを使用できます。 ここでは、結果は、返される結果の大規模なセットを待っている間に実行がブロックされないように、非同期ワークフローを使用してにページに返します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

今すぐ実行するこの計算に同期的に。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>エンティティを削除します。

取得した後は、エンティティを削除することができます。 エンティティを更新する場合と同様には取得した後にエンティティが変更される場合が失敗しました。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>テーブルを削除します。

ストレージ アカウントからテーブルを削除できます。 削除されたテーブルは、削除を後の一定期間の再作成するできなくなります。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>次の手順

これで、Table storage の基本を学習する次のリンクより複雑なストレージ タスクと、Azure Cosmos DB Table API について説明します。

- [Azure Cosmos DB Table API の概要](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [.NET リファレンス用ストレージ クライアント ライブラリ](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Azure Storage 型プロバイダー](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure Storage チーム ブログ](https://blogs.msdn.com/b/windowsazurestorage/)
- [接続文字列の構成](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [.NET で Azure Table Storage の概要](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
