---
title: 値型と参照型
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: f25caec43b7118b7b64db1b14516b0c5ea80f4f6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504882"
---
# <a name="value-types-and-reference-types"></a>値型と参照型
Visual Basic における型の 2 種類があります。 参照型と値の型。 参照型の変数はデータ (オブジェクト) への参照を格納するのに対して、値型の変数はデータを直接格納します。 参照型の場合、2 つの変数が同じオブジェクトを参照できるため、ある変数に対する演算によって、他の変数が参照しているオブジェクトが影響を受ける可能性があります。 各変数が独自のデータのコピーを値型の場合とに影響を与えるもう 1 つの変数に対する操作のことはできません (の場合を除く、 [ByRef パラメーター修飾子](../../../language-reference/modifiers/byref.md))。
  
## <a name="value-types"></a>値型  
 データ型は、*値の型*独自のメモリ割り当て内のデータを保持している場合。 値の型を以下に示します。  
  
- すべての数値データ型  
  
- `Boolean`、 `Char`、および `Date`  
  
- そのメンバーが参照型の場合でも、すべての構造  
  
- 列挙型では、その基になる型は常にため`SByte`、 `Short`、 `Integer`、 `Long`、 `Byte`、 `UShort`、 `UInteger`、または `ULong`  
  
 すべての構造体は参照型のメンバーが含まれている場合でも、値型です。 このため、値などの型`Char`と`Integer`.NET Framework の構造体によって実装されます。  
  
 たとえば、予約済みキーワードを使用して値の型を宣言する`Decimal`します。 使用することも、`New`値型を初期化するキーワード。 これは、型パラメーターを受け取るコンス トラクターがある場合に特に便利です。 この例は、<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>コンス トラクターは、新しいビルド`Decimal`指定した部分からの値。  
  
## <a name="reference-types"></a>参照型  
 A*参照型*データへの参照を格納します。 参照型を以下に示します。  
  
- `String`  
  
- その要素が値型の場合でも、すべての配列  
  
- などのクラス型します。 <xref:System.Windows.Forms.Form>  
  
- デリゲート  
  
 クラスは、*参照型*します。 場合でも、そのメンバーが値型は、すべての配列が参照型であるに注意してください。  
  
 使用する必要がありますすべての参照型は、基になる .NET Framework クラスを表すため、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)初期化するときに、キーワード。 次のステートメントでは、配列を初期化します。  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>型ではない要素  
 これらのいずれかとして宣言された要素のデータ型を指定できないため、次のプログラミング要素は、型とは見なされません。  
  
- 名前空間  
  
- モジュール  
  
- イベント  
  
- プロパティやプロシージャ  
  
- 変数、定数、およびフィールド  
  
## <a name="working-with-the-object-data-type"></a>オブジェクトのデータ型の操作  
 変数に参照型または値型のいずれかを割り当てることができます、`Object`データ型。 `Object`変数は常に、データ自体ではない、データへの参照を保持します。 ただし、値の型を割り当てた場合、`Object`変数、その場合と同様、独自のデータを保持します。 詳細については、次を参照してください。 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)します。  
  
 かどうかを見つけることができます、`Object`に渡すことによって変数が参照型または値型として機能する、<xref:Microsoft.VisualBasic.Information.IsReference%2A>メソッドで、<xref:Microsoft.VisualBasic.Information>のクラス、<xref:Microsoft.VisualBasic?displayProperty=nameWithType>名前空間。 <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> 返します`True`場合のコンテンツ、`Object`変数は参照型を表します。  
  
## <a name="see-also"></a>関連項目

- [null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [データ型の有効な使用方法](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
