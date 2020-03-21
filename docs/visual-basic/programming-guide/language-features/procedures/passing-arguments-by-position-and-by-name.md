---
title: 位置と名前による引数渡し
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401437"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>位置と名前による引数渡し (Visual Basic)

または`Sub``Function`プロシージャを呼び出すときは、プロシージャの定義に表示される順序で引数を*位置*によって渡したり、位置に関係なく*名前で*渡したりできます。

引数を名前で渡す場合は、引数の宣言名の後にコロンと等号 ( )`:=`を指定し、その後に引数値を指定します。 名前付き引数は任意の順序で指定できます。

たとえば、次`Sub`のプロシージャは 3 つの引数をとります。

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

このプロシージャを呼び出すときは、位置、名前、または両方を組み合わせて使用して引数を指定できます。

## <a name="passing-arguments-by-position"></a>位置による引数の引き渡し

次の例に`Display`示すように、引数を位置によって渡し、コンマで区切ってメソッドを呼び出すことができます。

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

位置指定引数リストで省略可能な引数を省略する場合は、その位置をコンマで保持する必要があります。 次の例では、`Display`引数なしでメソッド`age`を呼び出します。

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>名前による引数の引き渡し

または、次の例に`Display`示すように、名前で渡される引数をコンマで区切って呼び出すこともできます。

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

この方法で引数を名前で渡すと、複数の省略可能な引数を持つプロシージャを呼び出す場合に特に便利です。 引数を名前で指定する場合は、連続したコンマを使用して、位置引数が欠落していないことを示す必要はありません。 引数を名前で渡すと、渡す引数と省略する引数を簡単に追跡できます。

## <a name="mixing-arguments-by-position-and-by-name"></a>位置と名前による引数の混在

次の例に示すように、1 回のプロシージャ呼び出しで、位置と名前の両方で引数を指定できます。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

前の例では、省略された`age`引数の場所を保持するために余分なコンマ`birth`は必要ありません。

15.5 より前のバージョンの Visual Basic では、位置と名前を組み合わせて引数を指定する場合は、すべて最初に位置引数を指定する必要があります。 引数を名前で指定したら、残りの引数はすべて名前で渡す必要があります。  たとえば、次のメソッドの呼び`Display`出しは、コンパイラ エラー [BC30241: 名前付き引数が必要です](../../../misc/bc30241.md)。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

Visual Basic 15.5 以降では、位置引数の末尾が正しい位置にある場合は、位置指定引数を名前付き引数に続けることができます。 Visual Basic 15.5 でコンパイルすると、メソッドの前`Display`の呼び出しは正常にコンパイルされ、コンパイラ エラー [BC30241](../../../misc/bc30241.md)が生成されなくなります。

名前付き引数と位置指定引数を任意の順序で組み合わせてマッチングする機能は、コードを読みやすくするために名前付き引数を使用する場合に特に便利です。 たとえば、次`Person`のクラス コンストラクターには、 の両方`Person`を使用できる 2`Nothing`つの型の引数が必要です。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

名前付き引数と位置引数を混在させると、`father`と`mother`引数の値が : `Nothing`

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

名前付き引数を使用して位置指定引数に従うには、Visual Basic プロジェクト (.vbproj)\*ファイルに次の要素を追加する必要があります。

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

詳細については、「 [Visual Basic 言語バージョンの設定](../../../language-reference/configure-language-version.md)」を参照してください。

## <a name="restrictions-on-supplying-arguments-by-name"></a>名前による引数の指定に関する制限

引数を名前で渡して、必須の引数を入力しないようにすることはできません。 省略可能な引数のみを省略できます。

パラメータ配列を名前で渡すことはできません。 これは、プロシージャを呼び出すときに、パラメーター配列に対してコンマ区切りの引数を不特定多数指定し、コンパイラが 1 つの名前に複数の引数を関連付けることができないためです。

## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [オプションのパラメータ](./optional-parameters.md)
- [パラメータ配列](./parameter-arrays.md)
- [オプション](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
