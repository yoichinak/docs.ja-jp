---
title: '方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会します。'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: a88171d86ad820870ee72d224415d96931066abe
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593300"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会します。
この例は、指定された一連の単語と一致する文言を含む文をテキスト ファイルから検索する方法を示しています。 この例では検索語句の配列をハードコーディングしていますが、実行時に動的に設定することもできます。 この例のクエリを実行すると、"Historically"、"data"、"integrated" という単語をすべて含んだ文が返されます。  
  
## <a name="example"></a>例  
  
```vb  
Class FindSentences  
  
    Shared Sub Main()  
        Dim text As String = "Historically, the world of data and the world of objects " &   
        "have not been well integrated. Programmers work in C# or Visual Basic " &   
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &   
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &   
        "are tables, columns, rows, nodes, and separate languages for dealing with " &   
        "them. Data types often require translation between the two worlds; there are " &   
        "different standard functions. Because the object world has no notion of query, a " &   
        "query can only be represented as a string without compile-time type checking or " &   
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &   
        "objects in memory is often tedious and error-prone."  
  
        ' Split the text block into an array of sentences.  
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})  
  
        ' Define the search terms. This list could also be dynamically populated at runtime  
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}  
  
        ' Find sentences that contain all the terms in the wordsToMatch array  
        ' Note that the number of terms to match is not specified at compile time  
        Dim sentenceQuery = From sentence In sentences   
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                   StringSplitOptions.RemoveEmptyEntries)   
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()   
                            Select sentence  
  
        ' Execute the query  
        For Each str As String In sentenceQuery  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Class  
' Output:  
' Historically, the world of data and the world of objects have not been well integrated  
```  
  
 このクエリではまず、テキストを文単位に分割し、個々の単語を保持する文字列の配列に分割しています。 その各配列について、重複する単語を <xref:System.Linq.Enumerable.Distinct%2A> メソッドですべて削除したうえで、それらの単語の配列と `wordsToMatch` 配列との <xref:System.Linq.Enumerable.Intersect%2A> 演算を実行します。 共通部分のカウントと `wordsToMatch` 配列のカウントとが一致した場合、文を構成する単語内にすべての検索語句が見つかったものとして判断され、該当する文が返されます。  
  
 句読点を文字列から削除するために、<xref:System.String.Split%2A> の呼び出しでは句読点を区切り記号として使用しています。 この処理がないと、たとえば "Historically," という文字列があった場合に、`wordsToMatch` 配列内の "Historically" と一致しません。 ソース テキストに使われている句読点の種類によっては、別の区切り記号を使う必要があります。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
VB.NET コンソール アプリケーション プロジェクトを作成、 `Imports` System.Linq 名前空間のステートメント。
  
## <a name="see-also"></a>関連項目

- [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
