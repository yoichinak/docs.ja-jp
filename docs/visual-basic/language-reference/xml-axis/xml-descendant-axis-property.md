---
title: XML 子孫軸プロパティ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: f6d8a958b5a33c236ca5273cccda0e13693b564e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973536"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML 子孫軸プロパティ (Visual Basic)
次の子孫にアクセスできます。<xref:System.Xml.Linq.XElement>オブジェクト、<xref:System.Xml.Linq.XDocument>オブジェクト、コレクションの<xref:System.Xml.Linq.XElement>オブジェクト、または一連の<xref:System.Xml.Linq.XDocument>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a>指定項目  
 `object`  
 必須。 
  <xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションです。  
  
 ...<  
 必須。 子孫軸プロパティの開始を示します。  
  
 `descendant`  
 必須。 フォームにアクセスする子孫ノードの名前 [`prefix:]name`します。  
  
|パーツ|説明|  
|----------|-----------------|  
|`prefix`|任意。 子孫ノードの XML 名前空間プレフィックス。 使用して定義されているグローバル XML 名前空間にある必要があります、`Imports`ステートメント。|  
|`name`|必須。 子孫ノードのローカル名。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。|  
  
 \>  
 必須。 子孫軸プロパティの終了を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。  
  
## <a name="remarks"></a>Remarks  
 XML 子孫軸プロパティを使用して情報を取得する子孫ノードにアクセスすることができます、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトのコレクションから、または<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト。 XML を使用して、`Value`返されたコレクション内の最初の子孫ノードの値にアクセスするプロパティ。 詳細については、次を参照してください。 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)します。  
  
 Visual Basic コンパイラでは、descendant 軸のプロパティへの呼び出しに変換します、<xref:System.Xml.Linq.XContainer.Descendants%2A>メソッド。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 Descendant 軸のプロパティの名前をグローバルに宣言されている XML 名前空間のみを使用できます、`Imports`ステートメント。 XML 要素リテラル内でローカルに宣言されている XML 名前空間は使用できません。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。  
  
## <a name="example"></a>例  
 次の例は、という名前の最初の子孫ノードの値にアクセスする方法を示しています。`name`という名前のすべての子孫ノードの値と`phone`から、`contacts`オブジェクト。  
  
 [!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 XML リテラルを作成し、修飾名を持つ最初の子ノードの値にアクセスする次の名前空間のプレフィックスを使用して`ns:name`します。  
  
 [!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>関連項目
- <xref:System.Xml.Linq.XElement>
- [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
