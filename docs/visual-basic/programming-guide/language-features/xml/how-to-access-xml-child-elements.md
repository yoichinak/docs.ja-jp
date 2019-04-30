---
title: '方法: アクセスの XML 子要素 (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: cd1b0db5305c7879d89cfdfff6cd458d6dea14f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973031"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>方法: アクセスの XML 子要素 (Visual Basic)
この例では、軸のプロパティを XML 要素で指定した名前を持つすべての XML 子要素にアクセスする子を使用する方法を示します。 具体的を使用して、<xref:System.Xml.Linq.XElement.Value%2A>プロパティをコレクション内の最初の要素の値を取得、`name`子軸プロパティを返します。 `name`という名前のすべての子要素を取得する子軸プロパティ`phone`で、`contact`オブジェクト。 またこの例では、`phone`という名前のすべての子要素にアクセスする子軸プロパティ`phone`に格納されている、`contact`オブジェクト。  
  
## <a name="example"></a>例  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- <xref:System.Xml.Linq> 名前空間への参照  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [XML 子軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML Value プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Visual Basic での XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
