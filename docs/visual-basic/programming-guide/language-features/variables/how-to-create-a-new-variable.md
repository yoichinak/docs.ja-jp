---
title: '方法: 新しい変数を作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: a6cb7225ea203f0b38b731795684bfb0cfdfd2d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630902"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>方法: 新しい変数を作成する (Visual Basic)

変数を作成するには、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)を使用します。

### <a name="to-create-a-new-variable"></a>新しい変数を作成するには

1. `Dim`ステートメントで変数を宣言します。

    ```vb
    Dim newCustomer
    ```

2. [Private](../../../../visual-basic/language-reference/modifiers/private.md)、 [Static](../../../../visual-basic/language-reference/modifiers/static.md)、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)、 [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)など、変数の特性の仕様を含めます。 詳細については、「宣言された[要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)」を参照してください。

    ```vb
    Public Static newCustomer
    ```

    宣言で他のキーワード`Dim`を使用する場合、キーワードは必要ありません。

3. 仕様に従って変数の名前を指定します。これは Visual Basic の規則と規則に従う必要があります。 詳細については、次を参照してください。 [宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)

    ```vb
    Public Static newCustomer
    ```

4. 名前の後に As 句を使用し[て](../../../../visual-basic/language-reference/statements/as-clause.md)、変数のデータ型を指定します。

    ```vb
    Public Static newCustomer As Customer
    ```

    データ型を指定しない場合、既定値`Object`のが使用されます。

5. 句の`As`後に等号 (`=`) を付け、等号に続けて変数の初期値を指定します。

    Visual Basic は、 `Dim`ステートメントを実行するたびに、指定された値を変数に代入します。 初期値を指定しない場合、は、 `Dim`ステートメントが含まれているコードに最初に入力したときに、変数のデータ型の既定の初期値を Visual Basic 割り当てます。

    変数が参照型の場合は、 `As`句に[New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)キーワードを含めることで、そのクラスのインスタンスを作成できます。 を使用`New`しない場合、変数の初期値は[Nothing](../../../../visual-basic/language-reference/nothing.md)です。

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a>関連項目

- [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [ステートメント](../../../../visual-basic/language-reference/statements/index.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
