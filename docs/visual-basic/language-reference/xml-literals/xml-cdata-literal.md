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
ms.openlocfilehash: 01a505130d566ec88a6d87e5e9ad525e449d7298
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981245"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XCData>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>指定項目  
 `<![CDATA[`  
 必須。 XML CDATA セクションの開始を示します。  
  
 `content`  
 必須。 XML CDATA セクションに表示するテキスト コンテンツ。  
  
 `]]>`  
 必須。 セクションの終了を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XCData> オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 XML CDATA セクションを含む未加工のテキストが含まれている場合は、それを含んでいる XML を解析できません。 XML CDATA セクションは、任意のテキストを含めることができます。 これには、予約済み XML 文字が含まれます。 XML CDATA セクションは、シーケンスで終わる"] >"。 これは、次の点を意味します。  
  
-   埋め込み式の区切り記号が有効な XML の CDATA コンテンツであるので、XML CDATA リテラルの埋め込み式を使うことはできません。  
  
-   XML CDATA セクションは入れ子にできないため、`content`値を含めることはできません"] >"。  
  
 XML CDATA リテラルの変数を割り当てたり、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルでは、複数の行にまたがることができますが、行継続文字を使用しません。 これにより、XML ドキュメントの内容をコピーし、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラに、XML CDATA リテラルへの呼び出しに変換します、<xref:System.Xml.Linq.XCData.%23ctor%2A>コンス トラクター。  
  
## <a name="example"></a>例  
 次の例では、テキストを含む CDATA セクション"リテラルを含めることができます\<XML > タグ"。  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Xml.Linq.XCData>
- [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
