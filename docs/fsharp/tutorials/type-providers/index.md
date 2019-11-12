---
title: 'F# の関数型プログラミングの概要'
description: 'F# で関数型プログラミングの基礎を学習します。'
description: F# 型プロバイダーが、プログラムで使用する型、プロパティ、およびメソッドを提供するコンポーネントである方法を学ぶ
ms.date: 04/02/2018
ms.openlocfilehash: 5fa9de229caa2ec3ba4a248ca5cd1c8aa5adb230
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645166"
---
# <a name="type-providers"></a>型プロバイダー

F# 型プロバイダーは、プログラムで使用する型、プロパティ、およびメソッドを指定するコンポーネントです。 型プロバイダーは、F# コンパイラによって外部データソースに基づく **型を生成** します。

たとえば、SQL の F# 型プロバイダーは、リレーショナル データベースのテーブルと列を表す型を生成できます。 これは実際、[SQLProvider](https://fsprojects.github.io/SQLProvider/) 型プロバイダーが行うことです。

生成される型は、型プロバイダーへの入力パラメーターによって異なります。 サンプルデータソース (例えば JSON スキーマファイル) や、外部サービスを直接参照する URL、データ接続への接続文字列といったものがそのような入力になります。型プロバイダーは、型のグループがオンデマンドで展開されることを保証できます。つまり、その型が実際に参照される時に初めて展開されるのです。これによって、オンライン データ マーケットのような大規模な情報空間を直接オンデマンドで強く型付けされた方法で統合できます。

## <a name="generative-and-erased-type-providers"></a>生成型プロバイダーと消去型プロバイダー

型プロバイダーには生成と消去の 2 つの形式があります。

生成型プロバイダーは、生成されたアセンブリに .NET 型として書き込むことができる型を生成します。 これにより、他のアセンブリ内のコードから使用することができます。 つまり、データソースの型付き表現は一般に .NET 型で表現できるものでなければなりません。

消去型プロバイダーは、生成されたアセンブリまたはプロジェクトからのみ使用できる型を生成します。この型はアセンブリに書き込むことはなく、また他のアセンブリのコードから使用することができないため短期的であると言えます。 またこれらは **遅延** メンバーを含めることができ、潜在的に無限の情報空間の型を生成できます。これは大規模で相互接続されたデータソースの小さなサブセットを使う場合に便利です。

## <a name="commonly-used-type-providers"></a>一般的に使用される型プロバイダー

広く使用されている次のライブラリには、さまざまな用途の型プロバイダーが含まれています。

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) JSON、XML、CSV、および HTML ドキュメントの形式とリソースの型プロバイダーが含まれています。
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) オブジェクトマッピングとこれらのデータソースに対する F# LINQ クエリを通じて、リレーションデータベースへの強く型付けされたアクセスを提供します。
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) は、F# での T-SQL のコンパイル時にチェックされた埋め込みのための型プロバイダーのセットです。
- [Azure Storage Type provider](https://fsprojects.github.io/AzureStorageTypeProvider/) は、Azure Blob、Tables、および Queues の型を生成するため、プログラム全体でリソース名を文字列として指定することなく、これらのリソースにアクセスすることができます。
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) は URL によって指定された GraphQL サーバに基づく型を生成する **GraphQLProvider** を含みます。

必要に応じて、[独自のカスタム型プロバイダーを作成](creating-a-type-provider.md) したり他者のつくった型プロバイダーを参照できます。例えば、組織に多数の名前付きデータセットを提供するデータサービスがあり、それぞれに独自の安定したデータスキーマがあるとします。強く型付けされた方法で、スキーマを読み取り最新のデータセットをプログラマに提供する型プロバイダーを作成することができます。

## <a name="see-also"></a>関連項目

- [チュートリアル: 型プロバイダーを作成する](creating-a-type-provider.md)
- [F# 言語リファレンス](../../language-reference/index.md)
- [Visual F#](../../index.md)
