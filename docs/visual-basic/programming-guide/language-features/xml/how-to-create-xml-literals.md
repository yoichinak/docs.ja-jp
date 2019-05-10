---
title: '方法: XML リテラル (Visual Basic) を作成します。'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 991f10b00082bb4eb2b54f10c1b85cdc2c9009d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598537"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>方法: XML リテラル (Visual Basic) を作成します。
XML リテラルを使用して、XML ドキュメント、フラグメント、または要素をコード内で直接作成できます。 このトピックの例では、次の 3 つの子要素を持つ XML 要素を作成する方法と、XML ドキュメントを作成する方法を示します。  
  
 使用することも、 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Api を作成する[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。 詳細については、「 <xref:System.Xml.Linq.XElement> 」を参照してください。  
  
### <a name="to-create-an-xml-element"></a>XML 要素を作成するには  
  
- 実際の XML 構文と同じでは、XML リテラル構文を使用して XML インラインを作成します。  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     コードを実行します。 このコードの出力は次のとおりです。  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>XML ドキュメントを作成するには  
  
- XML ドキュメントのインラインを作成します。 次のコードは、リテラルの構文、XML 宣言、処理命令、コメント、および別の要素を格納する要素を含む XML ドキュメントを作成します。  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     コードを実行します。 このコードの出力は次のとおりです。  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>関連項目

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
