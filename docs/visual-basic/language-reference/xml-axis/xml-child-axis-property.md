---
title: XML Child Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 968154908bc6cb62bb221d42a1f71b329aa7096f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349462"
---
# <a name="xml-child-axis-property-visual-basic"></a>XML 子軸プロパティ (Visual Basic)
<xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションのいずれかの子にアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`object`|必須です。 <xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションです。|  
|.<|必須です。 子軸プロパティの開始を示します。|  
|`child`|必須です。 Name of the child nodes to access, of the form [`prefix:]name`.<br /><br /> -   `Prefix` - Optional. 子ノードの XML 名前空間プレフィックスです。 `Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。<br />-   `Name` - Required. ローカル子ノードの名前です。 See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|必須です。 子軸プロパティの終了を示します。|  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。  
  
## <a name="remarks"></a>Remarks  
 XML 子軸プロパティを使用すると、<xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションから子ノードに名前でアクセスできます。 返されるコレクションの最初の子ノードの値にアクセスするには、XML の `Value` プロパティを使用します。 For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 子軸プロパティの名前では、`Imports` ステートメントでグローバルに宣言されている XML 名前空間プレフィックスのみを使用できます。 XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。 For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>例  
 次の例は、`contact` オブジェクトの `phone` という名前の子ノードにアクセスする方法を示しています。  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>例  
 次の例は、`contacts` オブジェクトの `contact` 子軸プロパティによって返されたコレクションの、`phone` という名前の子ノードにアクセスする方法を示しています。  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement>
- [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
