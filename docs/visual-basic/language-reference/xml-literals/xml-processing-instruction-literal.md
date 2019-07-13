---
title: XML 処理命令リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3fbb16a4d47801b671d37566573215d3a57afff1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938607"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML 処理命令リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XProcessingInstruction>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>指定項目  
 `<?`  
 必須。 XML 処理命令リテラルの開始を示します。  
  
 `piName`  
 必須。 アプリケーションを示す処理命令のターゲットを名前します。 "Xml"または"XML"で始めることはできません。  
  
 `piData`  
 省略可能です。 アプリケーションの対象を示す文字列`piName`XML ドキュメントを処理する必要があります。  
  
 `?>`  
 必須。 処理命令の終了を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML 処理命令リテラルは、アプリケーションが XML ドキュメントを処理する方法を示します。 アプリケーションでは、XML ドキュメントが読み込まれる、アプリケーションは、ドキュメントを処理する方法を決定する XML 処理命令を確認できます。 アプリケーションの意味を解釈する`piName`と`piData`します。  
  
 XML ドキュメント リテラルには、XML 処理命令の次のような構文が使用されます。 詳細については、次を参照してください。 [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)します。  
  
> [!NOTE]
>  `piName`要素は、XML 1.0 仕様は、これらの id を予約するため、文字列"xml"または"XML"で始めることはできません。  
  
 変数に XML 処理命令リテラルを割り当てるまたは XML ドキュメント リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルでは、行継続文字をしなくても、複数の行をまたがることができます。 これにより、XML ドキュメントの内容をコピーし、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラへの呼び出しにリテラルの XML 処理命令を変換する、<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>コンス トラクター。  
  
## <a name="example"></a>例  
 次の例では、XML ドキュメントのスタイル シートを識別する処理命令を作成します。  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XProcessingInstruction>
- [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
