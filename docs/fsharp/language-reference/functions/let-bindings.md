---
title: let バインド
description: 使用する方法について説明します、 F# 'let' バインドの値または関数の識別子を関連付けます。
ms.date: 05/16/2016
ms.openlocfilehash: 45de82acf6f4423698cd8037266968e023f40dcb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941005"
---
# <a name="let-bindings"></a>let バインド

A*バインド*を値または関数と識別子を関連付けます。 使用する、`let`値または関数に名前をバインドするキーワード。

## <a name="syntax"></a>構文

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Remarks

`let`キーワード値または関数名の値を 1 つまたは複数定義する式のバインドで使用されます。 最も単純な形式、`let`式の名前からの単純な値の次のようにバインドします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

新しい行を使用して、識別子から式を分離する場合は、次のコードのように、式の各行をインデントする必要があります。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

名前だけではなく、名前を含むパターンを指定できますが、たとえば、タプル次のコードに示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*式の本体*名前が使用される式です。 式の本体が最初の文字と完全にする行にインデント、独自の行に表示されます、`let`キーワード。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

A`let`バインドに記述できるクラス型の定義で、またはローカルのスコープで、モジュール レベル関数の定義のようにします。 A`let`最上位レベルのモジュールまたはクラス型のバインドは、本文の式を指定する必要はありませんが、他のスコープ レベルでは、式の本体が必要です。 前に、任意の時点ではなくが、定義の時点より後バインド名は使用可能な`let`は次のコードに示すように、バインドが表示されます。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>関数のバインディング

関数バインドは関数バインドでは関数名をパラメーターでは、次のコードに示すように準じた値のバインディングの規則に従います。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

一般に、パラメーターは、タプル パターンなどのパターンです。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

A`let`最後の式の値に評価される式をバインドします。 そのため、次のコード例の値で`result`から計算`100 * function3 (1, 2)`に評価されます`300`します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

詳細については、「[関数](index.md)」を参照してください。

## <a name="type-annotations"></a>型の注釈

後にかっこで囲まれているすべての型名、コロン (:) を含めることによって、型パラメーターを指定できます。 最後のパラメーターの後にコロンと型を追加して、戻り値の型を指定することもできます。 完全な型注釈には、`function1`パラメーターの型として整数であるようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

明示的な型のパラメーターがない場合は、関数のパラメーターの種類を決定する型の推定が使用されます。 これをジェネリック パラメーターの型を自動的に一般化を含めることができます。

詳細については、次を参照してください。[自動ジェネリック化](../generics/automatic-generalization.md)と[型の推定](../type-inference.md)します。

## <a name="let-bindings-in-classes"></a>クラス内の let 束縛

A`let`構造体またはレコードの種類ではなく、クラス型にバインドを表示できます。 Let クラス型でバインディングを使用するには、クラスは、プライマリ コンス トラクターをいる必要があります。 コンス トラクターのパラメーターは、クラス定義内の型名の後に表示する必要があります。 A`let`クラス型のバインディングは、プライベート フィールドとそのクラス型と、と共にメンバーを定義します。`do`バインドの種類では、型のプライマリ コンス トラクターのコードをフォーム。 次のコード例は、クラスを表示する`MyClass`プライベート フィールドを持つ`field1`と`field2`します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

スコープ`field1`と`field2`は宣言されている型に制限されます。 詳細については、次を参照してください。 [ `let`クラス内のバインディング](../members/let-bindings-in-classes.md)と[クラス](../classes.md)します。

## <a name="type-parameters-in-let-bindings"></a>型パラメーターの let 束縛

A`let`型、またはコンピュテーション式で、モジュール レベルでバインドが明示的な型のパラメーターを持つことができます。 Let 関数の定義内など、式の中でバインディングには、型パラメーターを含めることはできません。 詳細については、「[ジェネリック](../generics/index.md)」を参照してください。

## <a name="attributes-on-let-bindings"></a>属性の let 束縛

属性は、最上位レベルに適用できる`let`モジュールに、次のコードに示すようにバインドします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>スコープとユーザー補助の Let バインド

Let によるバインドで宣言されたエンティティのスコープを含むの部分に制限されていますが、バインドが表示された後のスコープを (関数、モジュール、ファイル クラスなど)。 そのため、そのことが言えます let によるバインドがスコープに名前を導入します。 モジュールに let バインドされた値または関数モジュールのクライアントにアクセスできる限りは、モジュール内の let バインドは、モジュールのパブリック関数にコンパイルされるため、モジュールがアクセス可能で。 これに対し、let バインド クラスでは、クラスにプライベートです。

通常、モジュール内の関数は、クライアント コードで使用すると、モジュールの名前で修飾する必要があります。 たとえば、モジュール`Module1`関数があります`function1`、ユーザーは指定`Module1.function1`関数を参照します。

モジュールのユーザーは、インポート宣言を使用して、モジュール名によって修飾されることがなくそのモジュール内の関数を使用できるようにすることがあります。 先ほど説明した例では、モジュールのユーザー開くことができる場合、モジュールのインポート宣言のオープンを使用して`Module1`し、その後を参照してください`function1`直接します。

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

一部のモジュールは、属性を持つ[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)、つまり、モジュールの名前で公開されている関数を修飾する必要があります。 たとえば、F# List モジュールには、この属性があります。

モジュールとアクセス制御の詳細については、次を参照してください。[モジュール](../modules.md)と[アクセス制御](../access-control.md)します。

## <a name="see-also"></a>関連項目

- [関数](index.md)
- [クラス内の `let` バインド](../members/let-bindings-in-classes.md)