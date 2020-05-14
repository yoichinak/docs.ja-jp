---
title: XML CDATA リテラル
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 72e899e7bd30f2edf0e88207bb3b75bdf36fa11c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349432"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA リテラル (Visual Basic)
<xref:System.Xml.Linq.XCData> オブジェクトを表すリテラル。  
  
## <a name="syntax"></a>構文  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>指定項目  
 `<![CDATA[`  
 必須です。 XML CDATA セクションの先頭を表します。  
  
 `content`  
 必須です。 XML CDATA セクションに表示されるテキスト コンテンツ。  
  
 `]]>`  
 必須です。 セクションの末尾を表します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XCData> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML CDATA セクションには、未加工のテキストが含まれています。この未加工のテキストは XML に含める必要がありますが、そのテキストを含む XML で解析する必要はありません。 XML CDATA セクションには、任意のテキストを含めることができます。 予約済み XML 文字も含めることができます。 XML CDATA セクションの末尾には "]]>" シーケンスが使用されます。 これは以下を意味します。  
  
- 埋め込み式の区切り記号は有効な XML CDATA コンテンツであるため、XML CDATA リテラルでは埋め込み式を使用できません。  
  
- `content` には値 "]]>" を含めることができないため、XML CDATA セクションを入れ子にすることはできません。  
  
 XML CDATA リテラルは、変数に代入するか、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
> XML リテラルは複数行にまたがることができますが、行連結文字は使用されません。 これにより、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。  
  
 XML CDATA リテラルは、Visual Basic コンパイラによって、<xref:System.Xml.Linq.XCData.%23ctor%2A> コンストラクターへの呼び出しに変換されます。  
  
## <a name="example"></a>例  
 次の例では、"Can contain literal \<XML> tags" というテキストを含む CDATA セクションを作成します。  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XCData>
- [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
