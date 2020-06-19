---
title: '方法: ファイル、文字列、またはストリームからの XML の読み込み'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7a2a0513a066ae8ea8a70f7a5ae340ab29de7d25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330960"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>方法: ファイル、文字列、またはストリームから XML を読み込む (Visual Basic)

複数のメソッドを使用して、[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)を作成し、外部ソースからファイル、文字列、ストリームなどの内容を取り込むことができます。 以降の例でこれらのメソッドを示します。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>ファイルから XML を読み込むには

ファイルから <xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XDocument> オブジェクトなどの XML リテラルを取り込むには、`Load` メソッドを使用します。 このメソッドは、入力としてファイル パス、テキスト ストリーム、または XML ストリームを受け取ることができます。

次のコード例では、<xref:System.Xml.Linq.XDocument.Load%28System.String%29> メソッドを使用して、<xref:System.Xml.Linq.XDocument> オブジェクトにテキスト ファイルから XML を取り込む方法を示します。

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>文字列から XML を読み込むには

文字列から <xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XDocument> オブジェクトなどの XML リテラルを取り込むには、`Parse` メソッドを使用できます。

次のコード例では、<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> メソッドを使用して、<xref:System.Xml.Linq.XDocument> オブジェクトに文字列から XML を取り込む方法を示します。

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>ストリームから XML を読み込むには

ストリームから <xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XDocument> オブジェクトなどの XML リテラルを取り込むには、`Load` メソッドまたは <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> メソッドを使用できます。

次のコード例では、<xref:System.Xml.Linq.XNode.ReadFrom%2A> メソッドを使用して、<xref:System.Xml.Linq.XDocument> オブジェクトに XML ストリームから XML を取り込む方法を示します。

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
