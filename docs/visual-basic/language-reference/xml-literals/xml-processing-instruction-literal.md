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
ms.openlocfilehash: c589d3f4ac6bbb9aa9b2b8f2535888bddbf9c934
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958477"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML 処理命令リテラル (Visual Basic)
<xref:System.Xml.Linq.XProcessingInstruction>オブジェクトを表すリテラル。  
  
## <a name="syntax"></a>構文  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>指定項目  
 `<?`  
 必須。 XML 処理命令リテラルの開始を示します。  
  
 `piName`  
 必須。 処理命令が対象とするアプリケーションを示す名前。 "Xml" または "XML" で始めることはできません。  
  
 `piData`  
 省略可能です。 `piName`が対象とするアプリケーションで XML ドキュメントを処理する方法を示す文字列。  
  
 `?>`  
 必須。 処理命令の終了を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML 処理命令リテラルは、アプリケーションで XML ドキュメントを処理する方法を示します。 アプリケーションで XML ドキュメントが読み込まれると、アプリケーションは XML 処理命令を確認して、ドキュメントの処理方法を決定できます。 アプリケーションは、と`piName` `piData`の意味を解釈します。  
  
 XML ドキュメントリテラルでは、XML 処理命令と同様の構文を使用します。 詳細については、「 [XML ドキュメントリテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)」を参照してください。  
  
> [!NOTE]
> Xml `piName` 1.0 仕様ではこれらの識別子が予約されているため、要素の先頭に文字列 "xml" または "xml" を指定することはできません。  
  
 XML 処理命令リテラルを変数に割り当てるか、XML ドキュメントリテラルに含めることができます。  
  
> [!NOTE]
> XML リテラルは、行連結文字を必要とせずに、複数の行にまたがることができます。 これにより、XML ドキュメントからコンテンツをコピーし、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラは、XML 処理命令のリテラルをコンストラクターの<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>呼び出しに変換します。  
  
## <a name="example"></a>例  
 次の例では、XML ドキュメントのスタイルシートを識別する処理命令を作成します。  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XProcessingInstruction>
- [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
