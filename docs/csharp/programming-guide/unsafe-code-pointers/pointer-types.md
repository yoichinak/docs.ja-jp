---
title: ポインター型 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 7f04cfbac72008332a429c4e0ad8bd3f4e60cc83
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880326"
---
# <a name="pointer-types-c-programming-guide"></a>ポインター型 (C# プログラミング ガイド)

unsafe コンテキストの型には、ポインター型、値型、または参照型を設定できます。 ポインター型の宣言は、次のいずれかの形式になります。

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

ポインター型の `*` の前に指定された型は、**参照型**と呼ばれます。 次の型はいずれも参照型になります。

- 任意の整数型: [sbyte](../../language-reference/keywords/sbyte.md)、[byte](../../language-reference/keywords/byte.md)、[short](../../language-reference/keywords/short.md)、[ushort](../../language-reference/keywords/ushort.md)、[int](../../language-reference/keywords/int.md)、[uint](../../language-reference/keywords/uint.md)、[long](../../language-reference/keywords/long.md)、[ulong](../../language-reference/keywords/ulong.md)。
- 任意の浮動小数点型: [float](../../language-reference/keywords/float.md)、[double](../../language-reference/keywords/double.md)。
- [char](../../language-reference/keywords/char.md)。
- [bool](../../language-reference/keywords/bool.md)。
- [decimal](../../language-reference/keywords/decimal.md)。
- 任意の[列挙](../../language-reference/keywords/enum.md)型。
- 任意のポインター型。 `void**` などの式を使用できます。
- アンマネージ型のフィールドのみを含むユーザー定義の struct 型。

ポインター型は [object](../../language-reference/keywords/object.md) を継承せず、ポインター型と `object` の間で変換を行う方法はありません。 また、ボックス化とボックス化解除もポインターをサポートしません。 ただし、異なるポインター型の間で変換したり、ポインター型と整数型の間で変換したりすることはできます。

同じ 1 つの宣言で複数のポインターを宣言する場合、アスタリスク (*) は基底の型だけに記述します。各ポインター名のプレフィックスとしては使用しません。 次に例を示します。

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

オブジェクト参照は、それを指すポインターがあってもガベージ コレクションされる可能性があるため、ポインターによって参照や参照を含む[構造体](../../language-reference/keywords/struct.md)を指すことはできません。 ガベージ コレクターは、オブジェクトを指すポインター型があるかどうかを追跡しません。

`myType*` 型のポインター変数の値は、`myType` 型の変数のアドレスです。 ポインター型の宣言の例を次に示します。

|例|説明|
|-------------|-----------------|
|`int* p`|`p` は、整数へのポインターです。|
|`int** p`|`p` は、整数へのポインターのポインターです。|
|`int*[] p`|`p` は、整数へのポインターの 1 次元配列です。|
|`char* p`|`p` は、char へのポインターです。|
|`void* p`|`p` は、未知の型へのポインターです。|

ポインター間接演算子 * を使用すると、ポインター変数が指す位置にあるコンテンツにアクセスできます。 たとえば、次のような宣言があるとします。

```csharp
int* myVariable;
```

この例の式 `*myVariable` は、`int` に含まれているアドレスの位置にある `myVariable` 変数を示しています。

トピック「[fixed ステートメント](../../language-reference/keywords/fixed-statement.md)」および「[ポインター変換](../../programming-guide/unsafe-code-pointers/pointer-conversions.md)」に、ポインターの例がいくつか記載されています。 次の例は、`unsafe` キーワードと `fixed` ステートメントの使用例と、内部ポインターのインクリメント方法を示しています。  このコードは、コンソール アプリケーションの Main 関数に貼り付けて実行することができます  これらの例は、[-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを設定してコンパイルする必要があります。

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

間接演算子は、`void*` 型のポインターに適用できません。 ただし、void ポインターと他のポインター型はキャストを使用して相互に変換できます。

ポインターは、`null` にできます。 null ポインターに間接演算子を適用すると、実装で定義されている動作が発生します。

ポインターをメソッド間で引き渡すと、未定義の動作が発生する可能性があります。 たとえば、`in`、`out` または `ref` パラメーターを介してポインターをローカル変数に返したり、関数の結果として返したりするメソッドがあるとします。 ポインターが固定ブロックに設定されていた場合は、そのポインターが指す変数が既に固定されていない可能性があります。

次の表は、unsafe コンテキストでポインターに使用できる演算子とステートメントの一覧を示しています。

|演算子/ステートメント|使用|
|-------------------------|---------|
|`*`|ポインターの間接参照を実行します。|
|`->`|ポインター経由で構造体のメンバーにアクセスします。|
|`[]`|ポインターにインデックスを付けます。|
|`&`|変数のアドレスを取得します。|
|`++` および `--`|ポインターをインクリメントおよびデクリメントします。|
|`+` および `-`|ポインター演算を実行します。|
|`==`、`!=`、`<`、`>`、`<=`、`>=`|ポインターを比較します。|
|[`stackalloc` 演算子](../../language-reference/keywords/stackalloc.md)|スタックにメモリを割り当てます。|
|[`fixed` ステートメント](../../language-reference/keywords/fixed-statement.md)|変数を一時的に固定して、そのアドレスを取得できるようにします。|

ポインター関連の演算子について詳しくは、「[ポインターに関連する演算子](../../language-reference/operators/pointer-related-operators.md)」をご覧ください。

## <a name="c-language-specification"></a>C# 言語仕様

詳しくは、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の「[ポインター型](~/_csharplang/spec/unsafe-code.md#pointer-types)」をご覧ください。

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [アンセーフ コードとポインター](index.md)
- [ポインター変換](pointer-conversions.md)
- [型](../../language-reference/keywords/types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
