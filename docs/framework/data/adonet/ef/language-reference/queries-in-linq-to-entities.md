---
title: LINQ to Entities でのクエリ
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 3144796dfb1a970152d8ae56424aa37592d5da09
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848783"
---
# <a name="queries-in-linq-to-entities"></a>LINQ to Entities でのクエリ
クエリは、データ ソースからデータを取得する式です。 一般に、クエリは専用のクエリ言語で表現されます。たとえば、リレーショナル データベースであれば SQL、XML であれば XQuery が使用されます。 そのため、開発者はクエリの対象となるデータ ソースやデータ形式ごとに新しいクエリ言語を習得する必要があります。 統合言語クエリ (LINQ) は、データ ソースや形式の違いを意識することなくデータを扱うことのできる、より簡素化された一貫したモデルを提供します。 LINQ クエリでは、常にプログラミング オブジェクトを操作することになります。  
  
 LINQ のクエリ操作は、データ ソースを取得し、クエリを作成して、クエリを実行するという 3 つのアクションから成ります。  
  
 LINQ を介したクエリは、<xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスまたは <xref:System.Linq.IQueryable%601> ジェネリック インターフェイスを実装するデータ ソースに対して行うことができます。 ジェネリック インターフェイスを実装<xref:System.Data.Objects.ObjectQuery%601>するジェネリック<xref:System.Linq.IQueryable%601>クラスのインスタンスは、LINQ to Entities クエリのデータ ソースとして機能します。 <xref:System.Data.Objects.ObjectQuery%601> ジェネリック クラスは、0 個以上の型指定されたオブジェクトのコレクションを返すクエリを表します。 C# キーワード`var`(Visual Basic では Dim) を使用して、コンパイラにエンティティの型を推論させることもできます。  
  
 クエリでは、データ ソースから取得する情報を正確に指定できます。 また、並べ替え、グループ化、整形方法を指定して情報を取得することもできます。 LINQ では、クエリが変数に格納されます。 クエリが一連の値を返す場合、クエリ変数そのものがクエリ可能な型であることが必要です。 このクエリ変数は、クエリの情報を保存するだけで、なんらかのアクションを実行したり、データを返したりすることはありません。 クエリを作成した後、データを取得するには、そのクエリを実行する必要があります。  
  
## <a name="query-syntax"></a>クエリ構文  
 LINQ to Entities クエリは、クエリ式の構文とメソッド ベースのクエリ構文という 2 とおりの構文を使って作成できます。 クエリ式の構文は、C# 3.0 および Visual Basic 9.0 で新たに導入され、Transact-SQL や XQuery などと同様な宣言型の構文で記述された一連の句で構成されます。 ただし、.NET Framework 共通言語ランタイム (CLR) は、クエリ式の構文自体を読み取ることができません。 そのため、クエリ式はコンパイル時に、CLR が理解できる形式 (メソッド呼び出し) へと変換されます。 これらのメソッドは、*標準クエリ演算子*と呼ばれます。 開発者は、クエリ構文を使う代わりに、メソッド構文を使ってそれらを直接呼び出すこともできます。 詳細については、「[LINQ でのクエリ構文とメソッド構文](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」を参照してください。  
  
### <a name="query-expression-syntax"></a>クエリ式の構文  
 クエリ式は宣言型のクエリ構文です。 開発者は、Transact-SQL に似た形式の高級言語でクエリを記述できます。 クエリ式の構文を使用することにより、フィルター、並べ替え、グループ化など、データ ソースに対するきわめて複雑な処理を最小限のコードで実行できます。 詳細については、[基本的なクエリ操作 (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)を参照してください。 クエリ式構文の使用方法を示す例については、次のトピックを参照してください。  
  
- [クエリ式の構文例: 射影](query-expression-syntax-examples-projection.md)  
  
- [クエリ式の構文例: フィルター処理](query-expression-syntax-examples-filtering.md)  
  
- [クエリ式の構文例: 並べ替え](query-expression-syntax-examples-ordering.md)  
  
- [クエリ式の構文例: 集計演算子](query-expression-syntax-examples-aggregate-operators.md)  
  
- [クエリ式の構文例: パーティション分割](query-expression-syntax-examples-partitioning.md)  
  
- [クエリ式の構文例: 結合演算子](query-expression-syntax-examples-join-operators.md)  
  
- [クエリ式の構文例: 要素演算子](query-expression-syntax-examples-element-operators.md)  
  
- [クエリ式の構文例: グループ化](query-expression-syntax-examples-grouping.md)  
  
- [クエリ式の構文例: リレーションシップのナビゲーション](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>メソッド ベースのクエリ構文  
 LINQ to Entities クエリを構成するもう 1 つの方法は、メソッド ベースのクエリを使用することです。 メソッド ベースのクエリ構文は、LINQ の演算子メソッドを、ラムダ式をパラメーターとして直接順次呼び出すものです。 詳細については、「[ラムダ式](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。 メソッドベースの構文の使用方法を示す例については、次のトピックを参照してください。  
  
- [メソッド ベースのクエリ構文例: 射影](method-based-query-syntax-examples-projection.md)  
  
- [メソッド ベースのクエリ構文例: フィルター処理](method-based-query-syntax-examples-filtering.md)  
  
- [メソッド ベースのクエリ構文例: 並べ替え](method-based-query-syntax-examples-ordering.md)  
  
- [メソッド ベースのクエリ構文例: 集計演算子](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [メソッド ベースのクエリ構文例: パーティション分割](method-based-query-syntax-examples-partitioning.md)  
  
- [メソッド ベースのクエリ構文例: 変換](method-based-query-syntax-examples-conversion.md)  
  
- [メソッド ベースのクエリ構文例: 結合演算子](method-based-query-syntax-examples-join-operators.md)  
  
- [メソッド ベースのクエリ構文例: 要素演算子](method-based-query-syntax-examples-element-operators.md)  
  
- [メソッド ベースのクエリ構文例: グループ化](method-based-query-syntax-examples-grouping.md)  
  
- [メソッド ベースのクエリ構文例: リレーションシップのナビゲーション](method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>関連項目

- [エンティティへの LINQ](linq-to-entities.md)
- [C# の LINQ の概要](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Visual Basic の LINQ の概要](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [EF マージ オプションとコンパイル済みクエリ](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
