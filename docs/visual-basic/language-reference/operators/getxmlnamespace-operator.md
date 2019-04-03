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
ms.openlocfilehash: 757ca54e5ba370bf2cc48bc70499e7b43ec96ef6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834752"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace 演算子 (Visual Basic)
取得、<xref:System.Xml.Linq.XNamespace>指定された XML 名前空間プレフィックスに対応するオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>指定項目  
 `xmlNamespacePrefix`  
 省略可能です。 XML 名前空間プレフィックスを識別する文字列。 指定した場合、この文字列は有効な XML 識別子である必要があります。 詳細については、次を参照してください。[宣言されている XML 要素の名前と属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。 プレフィックスが指定されていない場合は、既定の名前空間が返されます。 既定の名前空間が指定されていない場合は、空の名前空間が返されます。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XNamespace> XML 名前空間のプレフィックスに対応するオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 `GetXmlNamespace`演算子を取得、 <xref:System.Xml.Linq.XNamespace> XML 名前空間のプレフィックスに対応するオブジェクト`xmlNamespacePrefix`します。  
  
 XML リテラルおよび XML 軸プロパティに直接 XML 名前空間プレフィックスを使用することができます。 ただし、使用する必要があります、`GetXmlNamespace`名前空間プレフィックスを変換する演算子、<xref:System.Xml.Linq.XNamespace>オブジェクトの前に、コードで使用することができます。 修飾されていない要素名を追加することができます、<xref:System.Xml.Linq.XNamespace>完全修飾を取得するオブジェクト<xref:System.Xml.Linq.XName>オブジェクト、どの多[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]メソッドが必要です。  
  
## <a name="example"></a>例  
 次の例ではインポート`ns`XML 名前空間プレフィックスとして。 XML リテラルを作成し、修飾の名前を持つ最初の子ノードにアクセスする次の名前空間のプレフィックスを使用して`ns:phone`します。 これは、後、その子ノードを渡します、`ShowName`サブルーチンを使用して、修飾名を構築します、`GetXmlNamespace`演算子。 `ShowName`サブルーチンは、修飾名を渡します、<xref:System.Xml.Linq.XNode.Ancestors%2A>親を取得するメソッドを`ns:contact`ノード。  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 呼び出すと`TestGetXmlNamespace.RunSample()`、次のテキストを含むメッセージ ボックスが表示されます。  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>関連項目

- [Imports ステートメント (XML 名前空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Visual Basic での XML へのアクセス](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
