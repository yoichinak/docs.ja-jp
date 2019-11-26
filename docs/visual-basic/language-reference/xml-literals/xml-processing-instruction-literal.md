---
title: XML 処理命令リテラル
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3602a81feae9287a77d060bb46f10eefee4fc05d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347046"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML 処理命令リテラル (Visual Basic)
A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.  
  
## <a name="syntax"></a>構文  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>指定項目  
 `<?`  
 必須です。 Denotes the start of the XML processing instruction literal.  
  
 `piName`  
 必須です。 Name indicating which application the processing instruction targets. Cannot begin with "xml" or "XML".  
  
 `piData`  
 省略可能です。 String indicating how the application targeted by `piName` should process the XML document.  
  
 `?>`  
 必須です。 Denotes the end of the processing instruction.  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML processing instruction literals indicate how applications should process an XML document. When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document. The application interprets the meaning of `piName` and `piData`.  
  
 The XML document literal uses syntax that is similar to that of the XML processing instruction. For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
> The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.  
  
 You can assign an XML processing instruction literal to a variable or include it in an XML document literal.  
  
> [!NOTE]
> An XML literal can span multiple lines without needing line continuation characters. This enables you to copy content from an XML document and paste it directly into a Visual Basic program.  
  
 The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.  
  
## <a name="example"></a>例  
 The following example creates a processing instruction identifying a style-sheet for an XML document.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XProcessingInstruction>
- [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
