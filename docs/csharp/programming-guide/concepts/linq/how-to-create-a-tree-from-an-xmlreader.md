---
title: 方法:XmlReader からツリーを作成する (C#)
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: f632bbdad7d52ea37e2587516792dfd13178d702
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593875"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>方法:XmlReader からツリーを作成する (C#)
このトピックでは、<xref:System.Xml.XmlReader> から直接 XML ツリーを作成する方法について説明します。 <xref:System.Xml.Linq.XElement> から <xref:System.Xml.XmlReader> を作成するには、<xref:System.Xml.XmlReader> を要素ノードに配置する必要があります。 <xref:System.Xml.XmlReader> はコメントや処理命令をスキップしますが、<xref:System.Xml.XmlReader> がテキスト ノードに配置されている場合はエラーがスローされます。 このようなエラーを回避するため、<xref:System.Xml.XmlReader> から XML ツリーを作成する前に、必ず <xref:System.Xml.XmlReader> を要素に配置してください。  
  
## <a name="example"></a>例  
 この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:書籍 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)」。  
  
 次のコードでは、`T:System.Xml.XmlReader` オブジェクトを作成し、最初の要素ノードが見つかるまでノードを読み取ります。 次に <xref:System.Xml.Linq.XElement> オブジェクトを読み込みます。  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
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

- [XML の解析 (C#)](./parsing-xml.md)
