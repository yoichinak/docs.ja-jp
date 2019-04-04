---
title: XML リテラルの概要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: a7b70669131ae35135088418e4b33b3ae289d322
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839887"
---
# <a name="xml-literals-overview-visual-basic"></a>XML リテラルの概要 (Visual Basic)
*XML リテラル*Visual Basic のコードに直接 XML を組み込むことができます。 XML リテラルの構文を表します[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト、およびそれには、XML 1.0 の構文に似ています。 これにより、簡単に、コードは、最終的な XML と同じ構造を持つため、XML 要素やドキュメントをプログラムで作成します。  
  
 Visual Basic XML リテラルをコンパイルする[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 統合し、簡単なオブジェクト モデルを作成すると、XML を操作し、このモデルを提供します。[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]します。 詳細については、「 <xref:System.Xml.Linq.XElement> 」を参照してください。  
  
 XML リテラルでは、Visual Basic の式を埋め込むことができます。 アプリケーションを作成、実行時に、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]各リテラルは、埋め込み式の値を組み込むためのオブジェクト。 これにより、XML リテラル内での動的なコンテンツを指定できます。 詳細については、[XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)を参照してください。  
  
 XML リテラルの構文と XML 1.0 の構文の違いの詳細については、[XML リテラルと XML 1.0 仕様](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)を参照してください。  
  
## <a name="simple-literals"></a>単純なリテラル  
 作成することができます、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]を入力するか、有効な XML に貼り付けることによって、Visual Basic コード内のオブジェクト。 リテラル XML 要素を返します、<xref:System.Xml.Linq.XElement>オブジェクト。 詳細については、[XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)と[XML リテラルと XML 1.0 仕様](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)を参照してください。 次の例では、いくつかの子要素を持つ XML 要素を作成します。  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 XML ドキュメントを作成するには、XML リテラルを起動して`<?xml version="1.0"?>`次の例のようにします。 XML ドキュメント リテラルを返します、<xref:System.Xml.Linq.XDocument>オブジェクト。 詳細については、[XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)を参照してください。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
>  Visual Basic で XML リテラルの構文は、XML 1.0 仕様での構文と同じです。 詳細については、[XML リテラルと XML 1.0 仕様](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)を参照してください。  
  
## <a name="line-continuation"></a>行の連結  
 XML リテラルは、行継続文字 (空白のアンダー スコアを入力してシーケンス) を使用せず複数の行にまたがることができます。 これにより、簡単に XML リテラルの XML ドキュメントを使用したコードを比較します。  
  
 コンパイラは、XML リテラルの一部として行継続文字を処理します。 属する場合にのみ空白-アンダー スコアを入力してシーケンスを使用する必要があります、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。  
  
 ただし、組み込み式に複数行の式がある場合は、行継続文字を必要がありますの操作を行います。 詳細については、[XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)を参照してください。  
  
## <a name="embedding-queries-in-xml-literals"></a>XML リテラルでクエリの埋め込み  
 埋め込み式の中では、クエリを使用できます。 これを行うときに、クエリによって返される要素が XML 要素に追加されます。 これにより、XML リテラルには、ユーザーのクエリの結果などの動的なコンテンツを追加できます。  
  
 次のコードは、埋め込みクエリを使用して、メンバーからの XML 要素を作成するなど、`phoneNumbers2`配列し、し、それらの要素の子として追加`contact2`します。  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>コンパイラが XML リテラルからオブジェクトを作成する方法  
 Visual Basic コンパイラでは、XML リテラルを変換と同等の呼び出しに[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]を構築するコンス トラクター、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。 Visual Basic コンパイラの呼び出しに次のコード例を変換できるなど、<xref:System.Xml.Linq.XProcessingInstruction>の XML バージョン命令は、コンス トラクターを呼び出し、<xref:System.Xml.Linq.XElement>のコンス トラクター、 `<contact>`、`<name>`と`<phone>`要素、およびへの呼び出し、<xref:System.Xml.Linq.XAttribute>のコンス トラクター、`type`属性。 具体的には、属性を指定すると、次のサンプルでは、Visual Basic コンパイラが呼び出す、<xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>コンス トラクターを 2 回クリックします。 最初は値を渡す`type`の`name`パラメーターと値を`home`の`value`パラメーター。 2 つ目は、値を渡すことも`type`の`name`パラメーターが、値`work`の`value`パラメーター。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement>
- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)
