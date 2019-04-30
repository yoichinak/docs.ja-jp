---
title: XML ツリー (Visual Basic) への要素、属性、およびノードの追加
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 35d3bdb27342dd7a871778ad4749db4d6849bd60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021857"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>XML ツリー (Visual Basic) への要素、属性、およびノードの追加
コンテンツ (要素、属性、コメント、処理命令、テキスト、および CDATA) を既存の XML ツリーに追加できます。  
  
## <a name="methods-for-adding-content"></a>コンテンツを追加するためのメソッド  
 次のメソッドを使用すると、<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument> に子コンテンツを追加できます。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<xref:System.Xml.Linq.XContainer> の子コンテンツの末尾にコンテンツを追加します。|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<xref:System.Xml.Linq.XContainer> の子コンテンツの冒頭にコンテンツを追加します。|  
  
 次のメソッドは、<xref:System.Xml.Linq.XNode> の兄弟ノードとしてコンテンツを追加します。 兄弟コンテンツの追加先となる最も一般的なノードは <xref:System.Xml.Linq.XElement> ですが、<xref:System.Xml.Linq.XText> や <xref:System.Xml.Linq.XComment> など別の種類のノードに、有効な兄弟コンテンツを追加することもできます。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<xref:System.Xml.Linq.XNode> の後にコンテンツを追加します。|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<xref:System.Xml.Linq.XNode> の前にコンテンツを追加します。|  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、2 つの XML ツリーを作成し、その 1 つを変更します。  
  
### <a name="code"></a>コード  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
```  
  
### <a name="comments"></a>コメント  
 このコードを実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a>関連項目

- [XML ツリー (LINQ to XML) の変更 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
