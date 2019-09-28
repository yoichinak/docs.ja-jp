---
title: '方法: 解析エラーのキャッチ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: a0c0749e8bc6d3fb1a71595778bfc5effaaf8533
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352931"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>方法: 解析エラーのキャッチ (Visual Basic)
このトピックでは、形式が正しくないか無効な XML を検出する方法について説明します。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] は、<xref:System.Xml.XmlReader> を使用して実装されます。 形式が正しくない XML や無効な XML が [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] に渡されると、基になる <xref:System.Xml.XmlReader> クラスから例外がスローされます。 XML を解析するさまざまなメソッド (<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> など) はこの例外をキャッチしません。この例外は、アプリケーションでキャッチできます。  
  
 XML リテラルを使用する場合は、解析エラーを検出できないことに注意してください。 Visual Basic コンパイラは、形式が正しくないか無効な XML をキャッチします。  
  
## <a name="example"></a>例  
 次のコードでは、無効な XML の解析を試行します。  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 このコードを実行すると、次の例外がスローされます。  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>、および <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> メソッドによってスローされる例外の詳細については、<xref:System.Xml.XmlReader> のドキュメントを参照してください。  
  
## <a name="see-also"></a>関連項目

- [XML の解析 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
