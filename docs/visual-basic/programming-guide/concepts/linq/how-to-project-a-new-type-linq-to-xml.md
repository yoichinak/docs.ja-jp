---
title: '方法: 新しい型を射影する (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 64b563c57406caae7869905c417db9e6439e6157
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318372"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>方法: 新しい型を射影する (LINQ to XML) (Visual Basic)
このセクションにあるその他の例では、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601> の `string`、および <xref:System.Collections.Generic.IEnumerable%601> の `int` として結果を返すクエリを示しています。 これらは一般的な戻り値の型ですが、すべてのシナリオに適切であるとは限りません。 多くの場合、クエリを使用して、別の型の <xref:System.Collections.Generic.IEnumerable%601> を返すようにする必要があります。  
  
## <a name="example"></a>例  
 この例では、`Select` 句でオブジェクトをインスタンス化する方法を示します。 コードでは、まずコンストラクターを使用して新しいクラスを定義し、次に、式が新しいクラスの新しいインスタンスになるように `Select` ステートメントを変更します。  
  
 この例では、「[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)」の XML ドキュメントを使用します。  
  
```vb  
Public Class NameQty  
    Public name As String  
    Public qty As Integer  
    Public Sub New(ByVal n As String, ByVal q As Integer)  
        name = n  
        qty = q  
    End Sub  
End Class  
  
Public Class Program  
    Shared Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
  
        Dim nqList As IEnumerable(Of NameQty) = _  
            From n In po...<Item> _  
            Select New NameQty( _  
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))  
  
        For Each n As NameQty In nqList  
            Console.WriteLine(n.name & ":" & n.qty)  
        Next  
    End Sub  
End Class  
```  
  
 この例では、「[方法: 単一の子要素を取得する (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)」で導入された `M:System.Xml.Linq.XElement.Element` メソッドを使用します。 また、キャストを使用して、`M:System.Xml.Linq.XElement.Element` メソッドによって返された要素の値を取得します。  
  
 この例を実行すると、次の出力が生成されます。  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>関連項目

- [プロジェクションと変換 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
