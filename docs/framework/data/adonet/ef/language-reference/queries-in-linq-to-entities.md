---
title: LINQ to Entities でのクエリ
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 561fa3217a80a8437b7c4d175d5a1156096ac241
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249558"
---
# <a name="queries-in-linq-to-entities"></a>LINQ to Entities でのクエリ
クエリは、データ ソースからデータを取得する式です。 一般に、クエリは専用のクエリ言語で表現されます。たとえば、リレーショナル データベースであれば SQL、XML であれば XQuery が使用されます。 そのため、開発者はクエリの対象となるデータ ソースやデータ形式ごとに新しいクエリ言語を習得する必要があります。 統合言語クエリ (LINQ) は、データ ソースや形式の違いを意識することなくデータを扱うことのできる、より簡素化された一貫したモデルを提供します。 LINQ クエリでは、常にプログラミング オブジェクトを操作することになります。  
  
 LINQ のクエリ操作は、データ ソースを取得し、クエリを作成して、クエリを実行するという 3 つのアクションから成ります。  
  
 LINQ を介したクエリは、<xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスまたは <xref:System.Linq.IQueryable%601> ジェネリック インターフェイスを実装するデータ ソースに対して行うことができます。 <xref:System.Data.Objects.ObjectQuery%601> ジェネリック<xref:System.Linq.IQueryable%601>インターフェイスを実装するジェネリッククラスのインスタンスは、LINQ to Entities クエリのデータソースとして機能します。 <xref:System.Data.Objects.ObjectQuery%601> ジェネリック クラスは、0 個以上の型指定されたオブジェクトのコレクションを返すクエリを表します。 また、 C#キーワード`var` (Dim in Visual Basic) を使用して、コンパイラでエンティティの型を推論することもできます。  
  
 クエリでは、データ ソースから取得する情報を正確に指定できます。 また、並べ替え、グループ化、整形方法を指定して情報を取得することもできます。 LINQ では、クエリが変数に格納されます。 クエリが一連の値を返す場合、クエリ変数そのものがクエリ可能な型であることが必要です。 このクエリ変数は、クエリの情報を保存するだけで、なんらかのアクションを実行したり、データを返したりすることはありません。 クエリを作成した後、データを取得するには、そのクエリを実行する必要があります。  
  
## <a name="query-syntax"></a>クエリ構文  
 LINQ to Entities クエリは、クエリ式の構文とメソッド ベースのクエリ構文という 2 とおりの構文を使って作成できます。 クエリ式の構文は 3.0 C#および Visual Basic 9.0 で新しく追加されたものであり、Transact-sql や XQuery に似た宣言型の構文で記述された一連の句で構成されています。 ただし、.NET Framework 共通言語ランタイム (CLR) は、クエリ式の構文自体を読み取ることができません。 そのため、クエリ式はコンパイル時に、CLR が理解できる形式 (メソッド呼び出し) へと変換されます。 これらのメソッドは、*標準クエリ演算子*と呼ばれます。 開発者は、クエリ構文を使う代わりに、メソッド構文を使ってそれらを直接呼び出すこともできます。 詳細については、「[LINQ でのクエリ構文とメソッド構文](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」を参照してください。  
  
### <a name="query-expression-syntax"></a>クエリ式の構文  
 クエリ式は宣言型のクエリ構文です。 開発者は、Transact-SQL に似た形式の高級言語でクエリを記述できます。 クエリ式の構文を使用することにより、フィルター、並べ替え、グループ化など、データ ソースに対するきわめて複雑な処理を最小限のコードで実行できます。 詳細については、「[基本的なクエリ操作 (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)」を参照してください。 クエリ式構文の使用方法を示す例については、次のトピックを参照してください。  
  
- [クエリ式の構文例:アイソメトリック](query-expression-syntax-examples-projection.md)  
  
- [クエリ式の構文例:除外](query-expression-syntax-examples-filtering.md)  
  
- [クエリ式の構文例:順番](query-expression-syntax-examples-ordering.md)  
  
- [クエリ式の構文例:集計演算子](query-expression-syntax-examples-aggregate-operators.md)  
  
- [クエリ式の構文例:パーティション](query-expression-syntax-examples-partitioning.md)  
  
- [クエリ式の構文例:結合演算子](query-expression-syntax-examples-join-operators.md)  
  
- [クエリ式の構文例:要素演算子](query-expression-syntax-examples-element-operators.md)  
  
- [クエリ式の構文例:分類](query-expression-syntax-examples-grouping.md)  
  
- [クエリ式の構文例:リレーションシップのナビゲート](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>メソッド ベースのクエリ構文  
 LINQ to Entities クエリを作成するもう1つの方法は、メソッドベースのクエリを使用することです。 メソッドベースのクエリ構文は、LINQ 演算子メソッドに対するダイレクトメソッド呼び出しのシーケンスであり、ラムダ式をパラメーターとして渡します。 詳細については、「[ラムダ式](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。 メソッドベースの構文の使用方法を示す例については、次のトピックを参照してください。  
  
- [メソッドベースのクエリ構文例:アイソメトリック](method-based-query-syntax-examples-projection.md)  
  
- [メソッドベースのクエリ構文例:除外](method-based-query-syntax-examples-filtering.md)  
  
- [メソッドベースのクエリ構文例:順番](method-based-query-syntax-examples-ordering.md)  
  
- [メソッドベースのクエリ構文例:集計演算子](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [メソッドベースのクエリ構文例:パーティション](method-based-query-syntax-examples-partitioning.md)  
  
- [メソッドベースのクエリ構文例:交換](method-based-query-syntax-examples-conversion.md)  
  
- [メソッドベースのクエリ構文例:結合演算子](method-based-query-syntax-examples-join-operators.md)  
  
- [メソッドベースのクエリ構文例:要素演算子](method-based-query-syntax-examples-element-operators.md)  
  
- [メソッドベースのクエリ構文例:分類](method-based-query-syntax-examples-grouping.md)  
  
- [メソッドベースのクエリ構文例:リレーションシップのナビゲート](method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>関連項目

- [LINQ to Entities](linq-to-entities.md)
- [C# の LINQ の概要](../../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Visual Basic の LINQ の概要](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Entity Framework マージオプションとコンパイル済みクエリ](https://go.microsoft.com/fwlink/?LinkId=199591)
