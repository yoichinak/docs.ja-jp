---
title: 比較演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 9014cac5e2f3933b27411dfe5681fc16f4cdde30
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821037"
---
# <a name="comparison-operators-visual-basic"></a>比較演算子 (Visual Basic)
Visual Basic で定義されている比較演算子を次に示します。  
  
 `<` 演算子  
  
 `<=` 演算子  
  
 `>` 演算子  
  
 `>=` 演算子  
  
 `=` 演算子  
  
 `<>` 演算子  
  
 [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like 演算子](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 これらの演算子は、それらが等しいかと、されない場合は、どのように異なるかどうかを判断する 2 つの式を比較します。 `Is`、 `IsNot`、および`Like`は個別のヘルプ ページに詳しく説明します。 関係比較演算子は、このページに詳しく説明します。  
  
## <a name="syntax"></a>構文  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 A`Boolean`比較の結果を表す値。  
  
 `expression`  
 必須。 任意の式。  
  
 `comparisonoperator`  
 必須。 すべての関係比較演算子です。  
  
 `object1`, `object2`  
 必須。 いずれかは、オブジェクト名を参照します。  
  
 `string`  
 必須。 任意のブール型 ( `String` ) の式を指定します。  
  
 `pattern`  
 必須。 すべて`String`式または文字の範囲。  
  
## <a name="remarks"></a>Remarks  
 次の表に、比較演算子と条件の一覧が含まれて かどうか`result`は`True`または`False`します。  
  
|演算子|`True`:|`False`:|  
|--------------|---------------|----------------|  
|`<` (より小さい)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=` (に等しいまたはそれよりも小さい)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>` (より大きい)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=` (より大きいまたは等しい)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=` (等しい)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>` (等しくない)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [演算子を =](../../../visual-basic/language-reference/operators/assignment-operator.md)代入演算子としても使用されます。  
  
 `Is`演算子、`IsNot`演算子、および`Like`演算子が前の表の演算子とは異なる特定の比較機能があります。  
  
## <a name="comparing-numbers"></a>数値を比較します。  
 型の式を比較するときに`Single`型のいずれかに`Double`、`Single`式に変換されます`Double`します。 この動作では、Visual Basic 6 で見られる動作とは逆です。  
  
 同様に、型の式を比較する`Decimal`型の式に`Single`または`Double`、`Decimal`式に変換されます`Single`または`Double`します。 `Decimal`式、小数部の値より小さい 1E-28 は失われる可能性があります。 このような小数部の値が失われるときに等しいと比較する 2 つの値があります。 このため、注意が必要と等しいかどうかを使用して (`=`) 2 つの浮動小数点変数を比較します。 2 つの数値の差の絶対値が許容差より小さいかどうかをテストすることができます。  
  
### <a name="floating-point-imprecision"></a>浮動小数点は誤差  
 浮動小数点数を使用する場合が常にないことを正確に表現メモリ内に留意してください。 値の比較などの特定の操作から予期しない結果に可能性と[Mod 演算子](../../../visual-basic/language-reference/operators/mod-operator.md)します。 詳細については、[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)を参照してください。  
  
## <a name="comparing-strings"></a>文字列の比較  
 依存する、アルファベット順の並べ替え順序に基づいて、文字列式を評価する文字列を比較したときに、`Option Compare`設定します。  
  
 `Option Compare Binary` ベースは文字列の文字の内部バイナリ表現から派生した並べ替え順序の比較です。 並べ替え順序は、コード ページによって決まります。 次の例では、通常、バイナリ並べ替え順序を示します。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` ベースは文字列で、アプリケーションのロケールによって決まる大文字のテキストの並べ替え順序の比較です。 設定すると`Option Compare Text`と前の例で文字を並べ替えるには、次のテキストの並べ替え順序が適用されます。  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>ロケールに依存せず  
 設定すると`Option Compare Text`、文字列比較の結果は、アプリケーションが実行されているロケールに依存できます。 2 つの文字は、別ではなく 1 つのロケールに等しいと比較可能性があります。 ログオンを試行を受け入れるかどうかなど、重要な決定を行う、文字列の比較を使用している場合は、ロケールと小文字の区別にアラートがあります。 設定するかを検討してください`Option Compare Binary`または呼び出し元、 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>、これは、ロケールが考慮されます。  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>関係比較演算子を省略したプログラミング  
 関係比較演算子の使用`Object`で式が許可されていません`Option Strict On`します。 ときに`Option Strict`は`Off`、どちらか`expression1`または`expression2`は、`Object`式、実行時の型の比較方法を決定します。 次の表は、式を比較する方法と、オペランドのランタイムの型に応じて、比較の結果を示します。  
  
|オペランドがある場合|比較では、|  
|---------------------|-------------------|  
|両方とも `String`|並べ替え文字列の並べ替えの特性に基づいて比較をします。|  
|両方の数値|オブジェクトに変換`Double`、数値比較します。|  
|1 つの数値型と 1 つ `String`|`String`に変換されます、`Double`数値比較を実行します。 場合、`String`に変換できない`Double`、<xref:System.InvalidCastException>がスローされます。|  
|どちらかまたは両方が以外の参照型です。 `String`|<xref:System.InvalidCastException> がスローされます。|  
  
 数値の比較処理`Nothing`0 として。 文字列比較を扱う`Nothing`として`""`(空の文字列)。  
  
## <a name="overloading"></a>オーバーロード  
 関係比較演算子 (`<`します。 `<=`、 `>`、 `>=`、 `=`、 `<>`) を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体できます動作を再定義オペランドは、そのクラスまたは構造体の型を持ちます。 コードは、このようなクラスまたは構造体で、これらの演算子のいずれかを使用している場合は、再定義された動作を理解することを確認します。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
 注意、[演算子を =](../../../visual-basic/language-reference/operators/assignment-operator.md)関係比較演算子としてのみ、代入演算子としてではなく、オーバー ロードされたを指定できます。  
  
## <a name="example"></a>例  
 次の例では、式の比較に使用する関係比較演算子は、のさまざまな使用を示します。 関係比較演算子を返す、`Boolean`結果を指定した式が評価されるかどうかを表す`True`します。 適用すると、`>`と`<`文字列演算子、比較を行う、文字列の通常のアルファベット順の並べ替え順序を使用しています。 この順序は、ロケール設定に依存することはできます。 並べ替えが大文字かどうかによって異なります、 [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)設定します。  
  
 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]  
  
 前の例では、最初に比較を返します`False`、残りの比較が戻って`True`します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.InvalidCastException>
- [= 演算子](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic における比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
