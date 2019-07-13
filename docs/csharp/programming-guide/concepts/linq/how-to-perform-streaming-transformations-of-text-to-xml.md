---
title: '方法: テキストから XML へのストリーミング変換を実行する (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: d37ea5167576098d4ea343e49ae4ff6bac20d4ba
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485249"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>方法: テキストから XML へのストリーミング変換を実行する (C#)
テキスト ファイルを処理する方法の 1 つは、`yield return` 構造を使用して、テキスト ファイルを一度に 1 行ずつストリーム出力する拡張メソッドを記述することです。 その後、テキスト ファイルをレイジー遅延方式で処理する LINQ クエリを記述できます。 次に <xref:System.Xml.Linq.XStreamingElement> を使用してストリーム出力すると、ソース テキスト ファイルのサイズにかかわらず、メモリを最小限しか使用しないテキスト ファイルから XML への変換を作成できます。  
  
 ストリーミング変換に関しては、いくつかの注意事項があります。 ストリーミング変換は、ファイル全体の処理を 1 回で行うことが可能で、かつソース ドキュメント内の順番どおりに行を処理できる場合に適しています。 ファイルを 2 回以上処理する必要がある場合、または処理前に行を並べ替える必要がある場合は、ストリーミングの手法が持つ多くの利点を活かすことはできません。  
  
## <a name="example"></a>例  
 次のテキスト ファイル (People.txt) は、この例のソースです。  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 次のコードには、このテキスト ファイルの行を遅延方式でストリーム出力する拡張メソッドが含まれています。  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
        while ((line = source.ReadLine()) != null)  
        {  
            yield return line;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
            from line in sr.Lines()  
            let items = line.Split(',')  
            where !line.StartsWith("#")  
            select new XElement("Person",  
                       new XAttribute("ID", items[0]),  
                       new XElement("First", items[1]),  
                       new XElement("Last", items[2]),  
                       new XElement("Occupation", items[3])  
                   )  
        );  
        Console.WriteLine(xmlTree);  
        sr.Close();  
    }  
}  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Person ID="1">  
    <First>Tai</First>  
    <Last>Yee</Last>  
    <Occupation>Writer</Occupation>  
  </Person>  
  <Person ID="2">  
    <First>Nikolay</First>  
    <Last>Grachev</Last>  
    <Occupation>Programmer</Occupation>  
  </Person>  
  <Person ID="3">  
    <First>David</First>  
    <Last>Wright</Last>  
    <Occupation>Inventor</Occupation>  
  </Person>  
</Root>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XStreamingElement>
