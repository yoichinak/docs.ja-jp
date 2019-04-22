---
title: 拡張インデクサー プロパティ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: a02c482db81d9d76752cfe66a292dc57c48b2acb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841264"
---
# <a name="extension-indexer-property-visual-basic"></a>拡張インデクサー プロパティ (Visual Basic)
コレクション内の個々の要素にアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```  
object(index)  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`object`|必須。 クエリ可能なコレクションです。 実装するコレクションは、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>します。|  
|(|必須。 インデクサーの開始を示します。|  
|`index`|必須。 コレクションの要素の 0 から始まる位置を指定する整数式。|  
|)|必須。 インデクサー プロパティの終了を示します。|  
  
## <a name="return-value"></a>戻り値  
 コレクション内の指定された場所からオブジェクトまたは`Nothing`場合は、インデックスが範囲外です。  
  
## <a name="remarks"></a>Remarks  
 拡張インデクサー プロパティを使用して、コレクション内の個々 の要素にアクセスすることができます。 このインデクサーは通常、XML 軸プロパティの出力で使用されます。 XML 子と XML 子孫軸プロパティのコレクションを返す<xref:System.Xml.Linq.XElement>オブジェクトまたは属性の値。  
  
 Visual Basic コンパイラは、拡張機能インデクサー プロパティをへの呼び出しに変換します、`ElementAtOrDefault`メソッド。 配列インデクサーとは異なり、`ElementAtOrDefault`メソッドを返します。`Nothing`場合は、インデックスが範囲外です。 この動作は、コレクション内の要素の数を簡単に判断できない場合に便利です。  
  
 このインデクサー プロパティを実装するコレクションの拡張機能プロパティのように、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>: コレクションには、インデクサーまたは既定のプロパティがあるない場合にのみ使用されます。  
  
 コレクションの最初の要素の値にアクセスする<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクト、XML を使用する`Value`プロパティ。 詳細については、次を参照してください。 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)します。  
  
## <a name="example"></a>例  
 次の例は、拡張機能インデクサーを使用して、2 番目の子ノードのコレクションにアクセスする方法を示しています。<xref:System.Xml.Linq.XElement>オブジェクト。 コレクションには、という名前のすべての子要素を取得する子軸プロパティを使用してアクセス`phone`で、`contact`オブジェクト。  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement>
- [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
