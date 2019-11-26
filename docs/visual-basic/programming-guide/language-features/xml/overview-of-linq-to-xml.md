---
title: LINQ to XML の概要
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 80d94ecb7dcc196ad831be7418bfecc785015cf9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346234"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic における LINQ to XML の概要
Visual Basic provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties. This enables you to use a familiar, convenient syntax for working with XML in your Visual Basic code. *XML literals* enable you to include XML directly in your code. *XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal. For more information, see [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) and [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is an in-memory XML programming API designed specifically to take advantage of [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Although you can call the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs directly, only Visual Basic enables you to declare XML literals and directly access XML axis properties.  
  
> [!NOTE]
> XML literals and XML axis properties are not supported in declarative code in an ASP.NET page. To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.  
  
 [Play button](./media/overview-of-linq-to-xml/play-video-icon-example.gif) For related video demonstrations, see [How Do I Get Started with LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) and [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).   
  
## <a name="creating-xml"></a>XML の作成  
 There are two ways to create XML trees in Visual Basic. You can declare an XML literal directly in code, or you can use the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs to create the tree. Both processes enable the code to reflect the final structure of the XML tree. For example, the following code example creates an XML element:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 For more information, see [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Accessing and Navigating XML  
 Visual Basic provides XML axis properties for accessing and navigating XML structures. These properties enable you to access XML elements and attributes by specifying the XML child element names. Alternatively, you can explicitly call the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] methods for navigating and locating elements and attributes. For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element. The code example uses a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to retrieve child elements and output them as XML elements, effectively performing a transform.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 For more information, see [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 Visual Basic enables you to specify an alias to a global XML namespace by using the `Imports` statement. The following example shows how to use the `Imports` statement to import an XML namespace:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.  
  
 You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Using XML Namespaces in XML Literals  
 The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 The Visual Basic compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute. When compiled, the code in the previous section's example produces essentially the same executable code as the following example:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Using XML Namespaces in XML Axis Properties  
 XML namespaces declared in XML literals are not available for use in XML axis properties. However, global namespaces can be used with the XML axis properties. Use a colon to separate the XML namespace prefix from the local element name. 例を次に示します。  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Visual Basic での XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
