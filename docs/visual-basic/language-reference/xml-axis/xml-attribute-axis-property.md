---
title: XML 属性軸プロパティ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 081359f32438c6474fe5c229634b60969e25a24e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965385"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML 属性軸プロパティ (Visual Basic)
属性の値にアクセスできるように、<xref:System.Xml.Linq.XElement>オブジェクトまたは最初の要素のコレクションを<xref:System.Xml.Linq.XElement>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>指定項目  
 `object`  
 必須。 <xref:System.Xml.Linq.XElement>オブジェクトまたは一連の<xref:System.Xml.Linq.XElement>オブジェクト。  
  
 .@  
 必須。 属性軸プロパティの開始を示します。  
  
 <  
 任意。 属性の名前の先頭を示すとき`attribute`Visual Basic では有効な識別子ではありません。  
  
 `attribute`  
 必須。 フォームにアクセスする属性の名前 [`prefix`:]`name`します。  
  
|パーツ|説明|  
|----------|-----------------|  
|`prefix`|任意。 属性の XML 名前空間プレフィックス。 
  `Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。|  
|`name`|必須。 属性のローカル名。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。|  
  
 \>  
 任意。 属性の名前の終了を示すとき`attribute`Visual Basic では有効な識別子ではありません。  
  
## <a name="return-value"></a>戻り値  
 値を格納する文字列`attribute`します。 属性名が存在しない場合`Nothing`が返されます。  
  
## <a name="remarks"></a>Remarks  
 XML 属性軸プロパティを使用してから、名前によって属性の値にアクセスすることができます、<xref:System.Xml.Linq.XElement>オブジェクトのコレクションの最初の要素からまたは<xref:System.Xml.Linq.XElement>オブジェクト。 名前、属性値を取得したり、前に新しい名前を指定することによって要素に新しい属性を追加、@ 識別子。  
  
 XML 属性を使用して参照するとき、文字列として @ 識別子、属性値が返され、明示的に指定する必要はありません、<xref:System.Xml.Linq.XAttribute.Value%2A>プロパティ。  
  
 XML 属性の名前付け規則は、Visual Basic 識別子の名前付け規則によって異なります。 有効な Visual Basic 識別子ではない名前を持つ XML 属性にアクセスするには、山かっこで名前を囲む (\<と >)。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 属性軸プロパティの名前を使用してグローバルに宣言されている XML 名前空間プレフィックスのみを使用できます、`Imports`ステートメント。 XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。  
  
## <a name="example"></a>例  
 次の例は、XML 属性の名前付きの値を取得する方法を示します`type`という名前の XML 要素のコレクションから`phone`します。  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>例  
 次の例は、ここでは、XML の動的なのインスタンスに属性を追加することでとの一部として、両方の XML 要素の属性を作成する方法を示します、<xref:System.Xml.Linq.XElement>オブジェクト。 `type`属性を宣言によって作成および`owner`属性が動的に作成されます。  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>例  
 次の例では、山かっこ構文を使用してという名前の XML 属性の値を取得`number-type`、Visual Basic では、有効な識別子ではないです。  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Phone type: work`  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 XML リテラルを作成し、修飾名を持つ最初の子ノードにアクセスする次の名前空間のプレフィックスを使用して"`ns:name`"。  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Phone type: home`  
  
## <a name="see-also"></a>関連項目
- <xref:System.Xml.Linq.XElement>
- [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
