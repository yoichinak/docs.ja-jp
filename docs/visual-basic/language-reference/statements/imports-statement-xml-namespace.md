---
title: Imports ステートメント - XML Namespace (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 97d08113a37477add9d770b0a680c303fe7e3040
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841408"
---
# <a name="imports-statement-xml-namespace"></a>Imports ステートメント (XML 名前空間)
XML リテラルおよび XML 軸のプロパティで使用するための XML 名前空間プレフィックスをインポートします。  
  
## <a name="syntax"></a>構文  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>指定項目  
 `xmlNamespacePrefix`  
 省略可能です。 XML 要素と属性を参照できます文字列`xmlNamespaceName`します。 いない場合`xmlNamespacePrefix`は既定の XML 名前空間がインポートされた XML 名前空間を指定します。 有効な XML 識別子である必要があります。 詳細については、[宣言されている XML 要素の名前と属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)を参照してください。  
  
 `xmlNamespaceName`  
 必須。 インポートされる XML 名前空間を識別する文字列。  
  
## <a name="remarks"></a>Remarks  
 使用することができます、 `Imports` XML リテラルおよび XML 軸のプロパティをまたはに渡されるパラメーターとして使用できるグローバルの XML 名前空間を定義するステートメント、`GetXmlNamespace`演算子。 (使用方法について、`Imports`型の名前を使用するコードで使用できるエイリアスをインポートするステートメントを参照してください[Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md))。使用して XML 名前空間を宣言する構文、`Imports`ステートメントは XML で使用される構文と同じです。 そのため、XML ファイルから名前空間宣言をコピーしで使用する`Imports`ステートメント。  
  
 XML 名前空間プレフィックスは、繰り返し、同じ名前空間からの XML 要素を作成する場合に便利です。 XML 名前空間プレフィックスが宣言された、`Imports`ステートメントがファイルにすべてのコードで使用可能であるという意味でグローバルです。 XML 要素リテラルおよび XML 軸のプロパティにアクセスするときに作成するときに使用することができます。 詳細については、[XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)と[XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)を参照してください。  
  
 名前空間プレフィックスなしのグローバル XML 名前空間を定義するかどうか (たとえば、 `Imports <xmlns="http://SomeNameSpace>"`)、その名前空間には、既定の XML 名前空間と見なされます。 既定の XML 名前空間は、任意の XML 要素リテラルまたは名前空間を明示的に指定されていない XML 属性軸プロパティに使用されます。 指定した名前空間が空の名前空間が場合、既定の名前空間が使用されます (つまり、 `xmlns=""`)。 既定の XML 名前空間は、XML リテラルの XML 属性または名前空間がない XML 属性軸プロパティには適用されません。  
  
 XML 名前空間、XML リテラルで定義されていると呼ばれる*ローカルの XML 名前空間*、XML 名前空間で定義されているよりも優先、`Imports`グローバルとしてステートメント。 XML 名前空間で定義されている、`Imports`ステートメント、Visual Basic プロジェクトのインポートされた XML 名前空間よりも優先されます。 XML リテラルには、XML 名前空間が定義されている場合、ローカルの名前空間は埋め込まれた式には適用されません。  
  
 グローバル名前空間は XML では、.NET Framework 名前空間と同じスコープと定義の規則に従います。 その結果、含めることができます、`Imports`ステートメント グローバル XML 名前空間を定義する .NET Framework 名前空間をインポートする任意の場所。 これには、コード ファイルとプロジェクト レベル インポートされた名前空間の両方が含まれます。 プロジェクト レベル インポートされた名前空間については、[参照設定 ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)を参照してください。  
  
 各ソース ファイルは、任意の数を含めることができます`Imports`ステートメント。 これらなどのオプションを宣言を従う必要があります、`Option Strict`ステートメント、およびそれらの前にプログラミング要素など`Module`または`Class`ステートメント。  
  
## <a name="example"></a>例  
 次の例では、既定の XML 名前空間とプレフィックスで識別される XML 名前空間のインポート`ns`します。 両方の名前空間を使用して、XML リテラルが作成されます。  
  
 [!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a>例  
 次の例は、XML 名前空間プレフィックスをインポート`ns`します。 名前空間プレフィックスを使用し、要素の最終的なフォームを表示する XML リテラルが作成されます。  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 コンパイラが、ローカル プレフィックス定義へのグローバル プレフィックスから XML 名前空間プレフィックスを変換されたことに注意してください。  
  
## <a name="example"></a>例  
 次の例は、XML 名前空間プレフィックスをインポート`ns`します。 その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>関連項目

- [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)
- [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [GetXmlNamespace 演算子](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
