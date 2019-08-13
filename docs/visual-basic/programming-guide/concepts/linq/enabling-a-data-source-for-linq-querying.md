---
title: LINQ Querying2 のデータソースを有効にする
ms.date: 07/20/2015
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
ms.openlocfilehash: 312a880158e4d9254d6ead81538dc9a17e5c31b0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "68959784"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>データ ソースの LINQ クエリの有効化

[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] を拡張して、データ ソースを [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] パターンでクエリできるようにする方法はいくつかあります。 データ ソースは、いくつか例を挙げると、データ構造体、Web サービス、ファイル システム、またはデータベースの場合があります。 クエリの構文とパターンは変わらないため、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] パターンを使用すると、クライアントは [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリが有効になっているデータ ソースを簡単にクエリできます。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] は、次の方法によってこれらのデータ ソースに拡張することができます。

- 型に <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装し、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] でその型のオブジェクト クエリを実行できるようにする。

- 型を拡張する <xref:System.Linq.Enumerable.Where%2A> や <xref:System.Linq.Enumerable.Select%2A> などの標準クエリ演算子メソッドを作成し、その型のカスタム [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを有効にする。

- データ ソース用に、<xref:System.Linq.IQueryable%601> インターフェイスを実装したプロバイダーを作成する。 このインターフェイスを実装したプロバイダーは、式ツリーの形式で [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを受け取ります。プロバイダーはこれをカスタマイズされた方法 (たとえばリモート) で実行できます。

- データ ソース用に、既存の [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] テクノロジを利用するプロバイダーを作成する。 そのようなプロバイダーは、クエリだけでなく、挿入、更新、および削除などの操作や、ユーザー定義型のマッピングも有効にします。

このトピックでは、これらのオプションについて説明します。

## <a name="how-to-enable-linq-querying-of-your-data-source"></a>データ ソースの LINQ クエリを有効にする方法

### <a name="in-memory-data"></a>インメモリ データ
 インメモリ データの [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを有効にする方法は 2 つあります。 データ型が <xref:System.Collections.Generic.IEnumerable%601> を実装する型の場合、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects を使用してデータをクエリすることができます。 <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装して型の列挙体を有効にしても意味がない場合は、その型の [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 標準クエリ演算子メソッドを定義するか、または型を拡張する [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 標準クエリ演算子メソッドを作成することができます。 標準クエリ演算子のカスタム実装は、結果を返すために遅延実行を使用する必要があります。

### <a name="remote-data"></a>リモート データ
 リモート データ ソースの [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを有効にするための最善の選択肢は、<xref:System.Linq.IQueryable%601> インターフェイスを実装することです。 しかしこれは、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] などのプロバイダーをデータ ソースに対して拡張することとは別です。 Visual Studio 2008 では、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] などの既存の [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] テクノロジを別の型のデータ ソースに拡張するためにプロバイダー モデルを使用することができません。

## <a name="iqueryable-linq-providers"></a>IQueryable LINQ プロバイダー
 <xref:System.Linq.IQueryable%601> を実装する [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] プロバイダーの複雑度にはかなりのばらつきがあります。 このセクションでは、さまざまなレベルの複雑度について説明します。

 複雑度が低めの `IQueryable` プロバイダーは、多くの場合、Web サービスの単一のメソッドとやり取りします。 この種のプロバイダーは処理するクエリに特定の情報を受け取るので非常に高い固有性を持ちます。 クローズされた型システムを持ち、おそらく 1 つの結果型を公開します。 クエリはほとんどの場合、標準クエリ演算子の <xref:System.Linq.Enumerable> 実装などを使用して、ローカルで実行されます。 複雑度が低めのプロバイダーは、クエリを表す式ツリーのメソッド呼び出し式を 1 つだけ調べ、残りのクエリのロジックは他の場所で処理されるようにします。

 複雑度が中レベルの `IQueryable` プロバイダーは、部分的に表現力が豊かなクエリ言語を持つデータ ソースを対象とします。 そのプロバイダーが Web サービスを対象とする場合、Web サービスの複数のメソッドとやり取りし、クエリが提示する問題に基づいて呼び出すメソッドを選択します。 中レベルの複雑度のプロバイダーは、簡単なプロバイダーより型システムが豊富ですが、それでもその種類は限られています。 たとえば、このレベルのプロバイダーは走査できる一対多リレーションシップを持つ型を公開する場合がありますが、ユーザー定義型のマッピング テクノロジは提供しません。

 `IQueryable` プロバイダーなどの複雑な [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] プロバイダーは [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ一式を、SQL などの表現力が豊かなクエリ言語に変換する場合があります。 複雑なプロバイダーは、それほど複雑でないプロバイダーより一般的です。これは、より多様な質問をクエリで処理できるためです。 さらに、オープンな型システムを持つため、ユーザー定義型をマップするために広範なインフラストラクチャを含める必要があります。 複雑なプロバイダーの開発には、多大な労力を要します。

## <a name="see-also"></a>関連項目

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
