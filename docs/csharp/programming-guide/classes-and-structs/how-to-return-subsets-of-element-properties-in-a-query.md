---
title: '方法: クエリで要素のプロパティのサブセットを返す - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 2c9fea2189819058187020c2e67b8826659fbed4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205445"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>方法: クエリで要素のプロパティのサブセットを返す (C# プログラミング ガイド)
次の両方の条件に当てはまる場合は、クエリ式に匿名型を使用します。  
  
- 各ソース要素のプロパティの一部のみを返したい。  
  
- クエリを実行したメソッドのスコープ外のクエリ結果を保存する必要がない。  
  
 各ソース要素の 1 つのプロパティまたはフィールドのみを返す場合は、`select` 句でドット演算子 (.) を使用します。 たとえば、各 `student` の `ID` のみを返すには、次のように `select` 句を記述します。  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>例  
 次に、匿名型を使用して、各ソース要素のプロパティのうち、指定した条件に一致するプロパティのみを返す例を示します。  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 名前を指定しない場合、匿名型にはプロパティのソース要素名が使用されます。 匿名型のプロパティに新しい名前を付けるには、次のように `select` ステートメントを記述します。  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 前の例でこの方法を試すには、`Console.WriteLine` ステートメントも次のように変更する必要があります。  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
このコードを実行するには、クラスをコピーし、System.Linq に `using` ディレクティブを使用した C# コンソール アプリケーションに貼り付けます。
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [匿名型](./anonymous-types.md)
- [LINQ クエリ式](../linq-query-expressions/index.md)
