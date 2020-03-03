---
title: let バインド
description: 識別子を値またはF#関数に関連付ける ' let ' バインドの使用方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 654631c7d1c48d8737e6098c98efee54cfdd91be
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630641"
---
# <a name="let-bindings"></a>let バインド

*バインド*は、識別子を値または関数に関連付けます。 キーワードを使用`let`して、名前を値または関数にバインドします。

## <a name="syntax"></a>構文

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Remarks

キーワード`let`は、1つまたは複数の名前の値または関数の値を定義するために、バインド式で使用されます。 `let`式の最も単純な形式は、次のように単純な値に名前をバインドします。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

新しい行を使用して識別子から式を分離する場合は、次のコードのように、式の各行をインデントする必要があります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

次のコードに示すように、名前だけでなく、名前を含むパターンを指定することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*本体式*は、名前が使用される式です。 本文の式は、 `let`キーワード内の最初の文字と正確に一致する行にインデントされています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

バインディング`let`は、モジュールレベル、クラス型の定義、またはローカルスコープ (関数定義など) で表示できます。 モジュール内の最上位レベルまたはクラス型のバインディングは、本体式を持つ必要はありませんが、その他のスコープレベルでは、本体式が必要です。`let` バインドされた名前は、次のコードに示すように、定義の時点`let`より後で使用できますが、バインドが表示される前の時点では使用できません。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>関数のバインド

関数のバインドは、次のコードに示すように、関数のバインドに関数名とパラメーターが含まれている点を除いて、値のバインドの規則に従います。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

一般に、パラメーターはタプルパターンなどのパターンです。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

バインド`let`式は、最後の式の値に評価されます。 したがって、次のコード例では、の`result`値はに`100 * function3 (1, 2)` `300`評価されるから計算されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

詳細については、「[関数](index.md)」を参照してください。

## <a name="type-annotations"></a>型の注釈

パラメーターの型は、コロン (:) を含めることによって指定できます。の後に型名が続き、すべてがかっこで囲まれています。 戻り値の型を指定するには、最後のパラメーターの後にコロンと型を追加します。 パラメーターの型とし`function1`て整数を持つの完全な型の注釈は、次のようになります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

明示的な型パラメーターがない場合は、型の推定を使用して、関数のパラメーターの型を決定します。 これには、ジェネリックにするパラメーターの型を自動的に一般化することが含まれます。

詳細については、「[自動汎](../generics/automatic-generalization.md)化と[型推論](../type-inference.md)」を参照してください。

## <a name="let-bindings-in-classes"></a>クラス内の let 束縛

バインド`let`はクラス型では表示できますが、構造体またはレコード型では使用できません。 クラス型で let バインドを使用するには、クラスにプライマリコンストラクターが必要です。 コンストラクターのパラメーターは、クラス定義の型名の後に記述する必要があります。 クラス`let`型のバインディングは、そのクラス型のプライベートフィールドとメンバーを定義し、型`do`のバインディングと共に、型のプライマリコンストラクターのコードを形成します。 次のコード例は、プライベート`MyClass`フィールド`field1`と`field2`を持つクラスを示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

`field1` と`field2`のスコープは、宣言されている型に制限されます。 詳細については、「クラスおよび[クラス](../classes.md) [ `let`のバインド](../members/let-bindings-in-classes.md)」を参照してください。

## <a name="type-parameters-in-let-bindings"></a>Let バインドの型パラメーター

モジュールレベル、型、またはコンピュテーション式内のバインディングは、明示的な型パラメーターを持つことができます。`let` 関数定義内などの式で let バインドを使用する場合、型パラメーターを指定することはできません。 詳細については、「[ジェネリック](../generics/index.md)」を参照してください。

## <a name="attributes-on-let-bindings"></a>Let バインドの属性

属性は、次のコードに示す`let`ように、モジュールの最上位のバインドに適用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Let バインドのスコープとアクセシビリティ

Let バインドを使用して宣言されたエンティティのスコープは、バインドが表示された後に、コンテナースコープ (関数、モジュール、ファイル、クラスなど) の部分に限定されます。 そのため、let バインドによって名前がスコープに導入されることがあります。 モジュールでは、モジュール内の let バインドがモジュールのパブリック関数にコンパイルされるので、モジュールがアクセス可能であればモジュールのクライアントが使用できるようになります。 これに対して、クラス内のバインディングはクラスに対してプライベートです。

通常、モジュール内の関数は、クライアントコードで使用するときに、モジュールの名前で修飾する必要があります。 たとえば、モジュール`Module1`に関数`function1`がある場合、ユーザーは関数を`Module1.function1`参照するように指定します。

モジュールのユーザーは、インポート宣言を使用して、モジュール名で修飾されていなくても、そのモジュール内の関数を使用できるようにすることができます。 前述の例では、モジュールのユーザーはインポート宣言`Module1`を使用してモジュールを開くことができ、その後は直接を`function1`参照します。

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

一部のモジュールには[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)属性があります。つまり、公開する関数がモジュールの名前で修飾されている必要があります。 たとえば、F# List モジュールには、この属性があります。

モジュールとアクセス制御の詳細については、「[モジュール](../modules.md)と[Access Control](../access-control.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [関数](index.md)
- [クラス内の `let` バインド](../members/let-bindings-in-classes.md)
