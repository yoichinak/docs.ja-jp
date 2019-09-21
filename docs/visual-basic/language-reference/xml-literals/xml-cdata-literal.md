---
title: XML CDATA リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 248f3cf31f686de3af2ea06012aa4a6d4f3f29fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942916"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA リテラル (Visual Basic)
<xref:System.Xml.Linq.XCData>オブジェクトを表すリテラル。  
  
## <a name="syntax"></a>構文  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>指定項目  
 `<![CDATA[`  
 必須。 XML CDATA セクションの先頭を示します。  
  
 `content`  
 必須。 XML CDATA セクションに表示されるテキストコンテンツ。  
  
 `]]>`  
 必須。 セクションの末尾を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XCData> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML CDATA セクションには未加工のテキストが含まれていますが、それを含む XML では解析できません。 XML CDATA セクションには、任意のテキストを含めることができます。 これには、予約済みの XML 文字が含まれます。 XML CDATA セクションは、シーケンス "]" > "で終了します。 これは、次の点を意味します。  
  
- 埋め込み式の区切り記号が有効な XML CDATA コンテンツであるため、XML CDATA リテラルで埋め込み式を使用することはできません。  
  
- XML CDATA セクションを入れ子に`content`することはできません。には値 "]] >" を含めることができません。  
  
 XML CDATA リテラルを変数に割り当てるか、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
> XML リテラルは複数の行にまたがることができますが、行連結文字は使用しません。 これにより、XML ドキュメントからコンテンツをコピーし、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラは、XML CDATA リテラルをコンストラクターの<xref:System.Xml.Linq.XCData.%23ctor%2A>呼び出しに変換します。  
  
## <a name="example"></a>例  
 次の例では、"リテラル\<XML > タグを含めることができます" というテキストを含む CDATA セクションを作成します。  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XCData>
- [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
