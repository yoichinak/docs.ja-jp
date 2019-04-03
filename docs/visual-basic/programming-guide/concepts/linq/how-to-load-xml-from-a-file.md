---
title: '方法: XML ファイルから読み込む (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
ms.openlocfilehash: b4f1f9abfa33b76e702b51221715da80c3f66421
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814962"
---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a>方法: XML ファイルから読み込む (Visual Basic)
このトピックでは、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> メソッドを使用して URI から XML を読み込む方法について説明します。  
  
## <a name="example"></a>例  
 次の例では、ファイルから XML ドキュメントを読み込む方法を示します。 この例では、books.xml を読み込んで、XML ツリーをコンソールに出力します。  
  
 この例では、XML ドキュメント、「[サンプル XML ファイル:書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md) を使用します。  
  
```vb  
Dim booksFromFile As XElement = XElement.Load("books.xml")  
Console.WriteLine(booksFromFile)  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```xml  
<Catalog>  
  <Book id="bk101">  
    <Author>Garghentini, Davide</Author>  
    <Title>XML Developer's Guide</Title>  
    <Genre>Computer</Genre>  
    <Price>44.95</Price>  
    <PublishDate>2000-10-01</PublishDate>  
    <Description>An in-depth look at creating applications   
      with XML.</Description>  
  </Book>  
  <Book id="bk102">  
    <Author>Garcia, Debra</Author>  
    <Title>Midnight Rain</Title>  
    <Genre>Fantasy</Genre>  
    <Price>5.95</Price>  
    <PublishDate>2000-12-16</PublishDate>  
    <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
  </Book>  
</Catalog>  
```  
  
## <a name="see-also"></a>関連項目

- [(Visual Basic) の XML の解析](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
