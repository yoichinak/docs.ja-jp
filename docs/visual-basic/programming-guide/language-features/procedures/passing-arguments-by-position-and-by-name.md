---
title: 位置と名前による引数渡し (Visual Basic)
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
ms.openlocfilehash: b872eda97d1e349ad781b12810e4b166d6e46fe1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837313"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>位置と名前による引数渡し (Visual Basic)
呼び出すと、`Sub`または`Function`プロシージャの引数を渡すことができます*位置によって*: プロシージャの定義で出現する順序で-渡すことができますか*名前で*、なし配置を考慮します。  
  
 引数には、名の後にコロンと等号 (=) が宣言されているのかを指定する引数を名前で渡す場合 (`:=`)、その後に、引数の値。 任意の順序で名前付き引数を指定することができます。  
  
 たとえば、次`Sub`手順は次の 3 つの引数を受け取ります。  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 このプロシージャを呼び出すときに、位置、名前、またはその両方の組み合わせを使用して引数を指定することができます。  
  
## <a name="passing-arguments-by-position"></a>位置による引数渡し  
 呼び出すことができます、`Display`メソッドとその引数が位置によって渡され、次の例に示すように、コンマで区切られます。  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 位置指定引数リストで省略可能な引数を省略した場合、コンマでは、その場所を保持する必要があります。 次の例では、`Display`メソッドなし、`age`引数。  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>名前による引数渡し  
 代わりに、呼び出すことができます`Display`名前によって渡される引数にもコンマで区切られた、次の例に示すようにします。  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 この方法で名前による引数渡しは、1 つ以上の省略可能な引数を持つプロシージャを呼び出す場合に特に便利です。 引数を名前で指定する場合は、引数の位置を示すために連続するコンマを使用する必要ありません。 名前による引数渡しやすく引数を渡し、省略しているものを追跡します。  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>位置と名前による引数の混在  

次の例に示すように、両方の位置と、1 つのプロシージャ呼び出しで名前による引数を指定できます。  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 前の例では、余分なコンマは省略された場所を保持するために必要な`age`引数のため`birth`は名前によって渡されます。  
  
15.5 前に、のバージョンの Visual Basic での位置と名前、位置指定引数の組み合わせで引数を指定するときにすべてあります最初。 名前で引数を指定すると、残りの引数する必要がありますすべてが名前によって渡されます。  たとえば、次の呼び出し、`Display`メソッドには、コンパイラ エラーが表示されます[BC30241:。名前付き引数が想定](../../../misc/bc30241.md)します。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

Visual Basic 15.5 以降では、位置指定引数は、名前付き引数終了位置指定引数が正しい位置にある場合。 Visual Basic 15.5 では、以前の呼び出しでコンパイルされた場合、`Display`メソッドが正常にコンパイルし、コンパイラ エラーを生成しなく[BC30241](../../../misc/bc30241.md)します。  

混在させるし、任意の順序で名前付きの位置指定引数と一致するこの機能は、コードを読みやすくする名前付き引数を使用する場合に特に便利です。 たとえば、次`Person`クラスのコンス トラクターには、型の 2 つの引数が必要です。 `Person`、どちらも指定できます`Nothing`します。 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

コードの意図をオフにときに混合の名前付きの位置指定引数を使用して、値の`father`と`mother`引数が`Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

名前付き引数を位置指定引数を実行するには、Visual Basic プロジェクトに次の要素を追加する必要があります (\*.vbproj) ファイル。

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

詳細については、次を参照してください。 [Visual Basic の言語バージョンを設定](../../../language-reference/configure-language-version.md)します。

## <a name="restrictions-on-supplying-arguments-by-name"></a>名前による引数渡しに関する制限事項  

必須の引数を入力せずに名前では、引数を渡すことはできません。 省略可能な引数のみを省略することができます。  
  
名前では、パラメーター配列を渡すことはできません。 これは、プロシージャを呼び出すときに、不特定数のパラメーター配列のコンマ区切りの引数を指定して、コンパイラは 1 つ以上の引数を 1 つの名前に関連付けることはできません。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [省略可能なパラメーター](./optional-parameters.md)
- [パラメーター配列](./parameter-arrays.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
