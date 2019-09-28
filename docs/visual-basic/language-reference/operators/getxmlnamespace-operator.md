---
title: GetXmlNamespace 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: bfccdcd9b5d35418b206dfa9fefffb5ddab69c66
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592165"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace 演算子 (Visual Basic)
指定した XML 名前空間プレフィックスに対応する @no__t 0 オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>指定項目  
 `xmlNamespacePrefix`  
 任意。 XML 名前空間プレフィックスを識別する文字列。 指定する場合、この文字列は有効な XML 識別子である必要があります。 詳細については、「宣言され[た XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。 プレフィックスが指定されていない場合は、既定の名前空間が返されます。 既定の名前空間が指定されていない場合は、空の名前空間が返されます。  
  
## <a name="return-value"></a>戻り値  
 XML 名前空間プレフィックスに対応する @no__t 0 オブジェクト。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 演算子は、XML 名前空間プレフィックス `xmlNamespacePrefix` に対応する @no__t 1 オブジェクトを取得します。  
  
 Xml 名前空間プレフィックスは、xml リテラルおよび XML 軸プロパティで直接使用できます。 ただし、コードで使用するには、`GetXmlNamespace` 演算子を使用して、名前空間プレフィックスを <xref:System.Xml.Linq.XNamespace> オブジェクトに変換する必要があります。 修飾されていない要素名を <xref:System.Xml.Linq.XNamespace> オブジェクトに追加して、完全修飾 <xref:System.Xml.Linq.XName> オブジェクトを取得できます。これには、多くの @no__t 2 つのメソッドが必要です。  
  
## <a name="example"></a>例  
 次の例では、`ns` を XML 名前空間プレフィックスとしてインポートします。 次に、名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名が `ns:phone` の最初の子ノードにアクセスします。 次に、その子ノードを @no__t 0 のサブルーチンに渡します。このサブルーチンは、`GetXmlNamespace` 演算子を使用して修飾名を構築します。 次に、@no__t 0 のサブルーチンは、修飾名を <xref:System.Xml.Linq.XNode.Ancestors%2A> メソッドに渡して、親 `ns:contact` ノードを取得します。  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 @No__t-0 を呼び出すと、次のテキストを含むメッセージボックスが表示されます。  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>関連項目

- [Imports ステートメント (XML 名前空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Visual Basic での XML へのアクセス](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
