---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 1a486d0fadce8135fe01d9eecd611081c986bfae
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647687"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
ある変数またはプロパティを読み込めるが書き込まれませんを指定します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="rules"></a>ルール  
  
- **宣言コンテキスト。** `ReadOnly` は、モジュール レベルでのみ使用できます。 これは、意味の宣言のコンテキストを`ReadOnly`要素は、クラス、構造体、またはモジュールにある必要があるあり、ソース ファイル、名前空間、またはプロシージャにすることはできません。  
  
- **結合された修飾子。** 指定することはできません`ReadOnly`と共に`Static`同じ宣言内。  
  
- **値を代入します。** コードの使用、`ReadOnly`プロパティは、その値を設定できません。 基になるストレージにアクセスするコードが割り当てるまたは値をいつでもでも変更します。  
  
     値を割り当てることができます、`ReadOnly`変数の宣言でのみ、またはクラスまたは構造体が定義されているのコンス トラクター。  
  
## <a name="when-to-use-a-readonly-variable"></a>読み取り専用の変数を使用する場合  
 状況を使用することはできません、 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)宣言して定数値を代入します。 たとえば、`Const`ステートメントで割り当てるには、必要なデータ型を受け付けないことがありますまたはコンパイル時に定数式で値を計算することができません。 コンパイル時に値をも認識していない可能性があります。 このような場合は、使用することができます、`ReadOnly`定数値を保持する変数。  
  
> [!IMPORTANT]
>  場合でも、変数自体がそのメンバーを変更できます、変数のデータ型が配列やクラスのインスタンスなど、参照型の場合`ReadOnly`します。 次に例を示します。  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 初期化されると、配列が指す`characterArray()`およびを保持"x"、"y"、"z"です。 変数`characterArray`は`ReadOnly`、初期化; であると、その値を変更することはできません、新しい配列を割り当てることはできません。 ただし、配列メンバーの 1 つ以上の値を変更することができます。 次のプロシージャの呼び出し`changeArrayElement`、によって示される配列`characterArray()`およびを保持"x"、"M"、"z"です。  
  
 これは、プロシージャのパラメーターを宣言することのような[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)、呼び出し元引数自体を変更できなくなります、プロシージャがそのメンバーを変更するようになります。  
  
## <a name="example"></a>例  
 次の例では、定義、`ReadOnly`従業員が雇用された日付のプロパティ。 プロパティの値として内部的にクラス ストア、`Private`クラス内部の変数、そして唯一のコードは、その値を変更できます。 ただし、このプロパティは`Public`、およびクラスにアクセスできる任意のコードは、プロパティを読み取ることができます。  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 `ReadOnly` 修飾子は、次のコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
