---
title: '方法 : XML リテラルに式を埋め込む'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332938"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>方法: XML リテラルに式を埋め込む (Visual Basic)
You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time. The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.  
  
 The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses. For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects. 詳細については、「<xref:System.Xml.Linq.XElement>」を参照してください。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-insert-text-as-element-content"></a>To insert text as element content  
  
- The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     この例を実行すると、次の出力が生成されます。  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>To insert text as an attribute value  
  
- The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     この例を実行すると、次の出力が生成されます。  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>To insert text for an element name  
  
- The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.  
  
     When creating elements by using this technique, you must close them with the \</> tag.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     この例を実行すると、次の出力が生成されます。  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>関連項目

- [方法: XML リテラルを作成する](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
