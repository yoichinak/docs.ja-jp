---
title: 型プロバイダー
description: 学習方法、F#型プロバイダーは、型、プロパティ、およびプログラムで使用するメソッドを提供するコンポーネント。
ms.date: 04/02/2018
ms.openlocfilehash: 39000fd1ca2af78afd1c333816fe9d5c0e2517cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967766"
---
# <a name="type-providers"></a>型プロバイダー

F# 型プロバイダーは、プログラムで使用する型、プロパティ、およびメソッドを指定するコンポーネントです。 型プロバイダー生成として知られる仕組み**指定された型が**、F# コンパイラによって生成され、外部データ ソースに基づきます。

たとえば、SQL の F# 型プロバイダーは、リレーショナル データベースのテーブルと列を表す型を生成できます。 これは実際には、どのような[SQLProvider](https://fsprojects.github.io/SQLProvider/)型プロバイダーは。

種類は、型プロバイダーへの入力パラメーターによって異なります。 提供されています。 このような入力には、JSON スキーマ ファイルなど)、サンプル データ ソースができるように、外部サービスまたはデータ ソースへの接続文字列を直接指す URL。 型プロバイダーは、オンデマンドの種類のグループが展開されるだけも確認できます。つまり、型が実際には、プログラムで参照されている場合、展開されます。 これにより、オンライン データ マーケットのような大規模な情報空間の直接的な、必要に応じた統合を厳密に型指定された方法で実現できます。

## <a name="generative-and-erased-type-providers"></a>当初、消去型プロバイダー

型プロバイダーは 2 つの形式があります。当初と消去されます。

当初の型プロバイダーは、生成されたアセンブリに .NET 型として書き込むことができる型を生成します。 これにより、他のアセンブリ内のコードから使用することができます。 意味、データ ソースの型指定された表現する必要があります一般に .NET 型で表現するは不可能である 1 つ。

消去型プロバイダーは、アセンブリまたはプロジェクトから生成されるでのみ利用できる型を生成します。 型は短期です。つまり、アセンブリには書き込まれませんが、他のアセンブリのコードで使用できることはできません。 含めることができます*遅延*メンバー、無限の可能性のある情報空間から使用して指定された型にできます。 大規模で相互接続されたデータ ソースの小さなサブセットを使用する場合に便利です。

## <a name="commonly-used-type-providers"></a>一般的に使用される型プロバイダー

広く使用されている次のライブラリには、さまざまな使用法の型プロバイダーが含まれます。

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) JSON、XML、CSV、および HTML ドキュメントの形式とリソースの型プロバイダーが含まれています。
- [SQLProvider](https://fsprojects.github.io/SQLProvider/)オブジェクトのマッピングと F# LINQ を使用する関係のデータベースへのアクセスを厳密に型指定されたこれらのデータ ソースに対するクエリを提供します。
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)一連の型プロバイダーがコンパイル時チェックが F# では、T-SQL の埋め込み。
- [Azure のストレージ型プロバイダー](https://fsprojects.github.io/AzureStorageTypeProvider/)型 Azure Blob、テーブル、およびキューは、リソース名をプログラム全体で文字列として指定することがなくこれらのリソースにアクセスすることができますを提供します。
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html)が含まれています、 **GraphQLProvider**URL で指定された GraphQL server に基づいて型を提供します。

できます必要に応じて、[独自のカスタム型プロバイダーを作成する](creating-a-type-provider.md)、または他のユーザーによって作成されている型プロバイダーを参照します。 たとえば、組織に 1 つのデータ サービスを用意し、そのデータ サービスにより、増加し続ける名前付きデータセット群と各データセットの安定したデータ スキーマを提供するとします。 スキーマを読み取り、利用可能な最新のデータセットを厳密に型指定してプログラマに提示する型プロバイダーを作成することもできます。

## <a name="see-also"></a>関連項目

- [チュートリアル: 型プロバイダーを作成します。](creating-a-type-provider.md)
- [F# 言語リファレンス](../../language-reference/index.md)
- [Visual F#](../../index.md)