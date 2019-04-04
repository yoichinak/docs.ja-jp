---
title: コンストラクター
description: 定義および F# で作成し、クラスと構造のオブジェクトを初期化するコンス トラクターを使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 34989e2877b29f6f9fe1f6cc05e3fd7c90a1306a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612076"
---
# <a name="constructors"></a>コンストラクター

このトピックでは、定義して作成し、クラスと構造のオブジェクトを初期化するコンス トラクターを使用する方法を説明します。

## <a name="construction-of-class-objects"></a>クラスのオブジェクトの構築

クラス型のオブジェクトでは、コンス トラクターがあります。 コンス トラクターの 2 種類があります。 型名の直後にかっこで囲まれたパラメーターを持つが表示される、プライマリ コンス トラクターは 1 つです。 使用して、他の省略可能な追加のコンス トラクターを指定する、`new`キーワード。 このような追加のコンス トラクターは、プライマリ コンス トラクターを呼び出す必要があります。

プライマリ コンス トラクターを含む`let`と`do`クラス定義の先頭にあるバインディング。 A`let`バインディング クラスのプライベート フィールドおよびメソッドの宣言を`do`バインド コードを実行します。 詳細については`let`クラスのコンス トラクター内のバインディングを参照してください[`let`クラス内のバインディング](let-bindings-in-classes.md)します。 詳細については`do`のコンス トラクターでバインドを参照してください[`do`クラス内のバインディング](do-bindings-in-classes.md)します。

使用してオブジェクトを作成するかどうかを呼び出したいコンス トラクターは、プライマリ コンス トラクターまたは追加のコンス トラクターに関係なく、`new`式の有無にかかわらず、省略可能な`new`キーワード。 コンマで区切られた順序で引数の一覧を作成するか、コンス トラクターの引数と共に、オブジェクトを初期化し、またはかっこで囲まれた名前付き引数と値を使用して、かっこで囲まれています。 できますもプロパティを設定して、オブジェクト、オブジェクトの構築時にプロパティ名を使用して、コンス トラクターの引数をという名前を使用すると同様に、値を割り当てる.

次のコードでは、クラス コンス トラクターとさまざまなオブジェクトを作成する方法を示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

出力は次のとおりです。

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>構造の構築

構造体では、クラスのすべての規則に従います。 そのため、プライマリ コンス トラクターがあることができを使用して追加のコンス トラクターを行うことができます`new`します。 ただし、構造体とクラスの 1 つの重要な違いがある: プライマリ コンス トラクターが定義されていない場合でも、構造体は既定のコンス トラクター (つまり、引数なしで 1 つ) を持つことができます。 既定のコンス トラクターでは、0 またはそれと同等では、通常は、その型の既定値をすべてのフィールドを初期化します。 コンス トラクターの構造を定義するには、既定のコンス トラクターと競合しないように、少なくとも 1 つの引数にすることが必要です。

また、構造体で多くの場合を使用して作成されるフィールドがあります、`val`キーワード; クラスは、これらのフィールドをこともできます。 構造体とクラスを使用して定義されているフィールドを持つ、`val`キーワード初期化することも追加のコンス トラクターでレコードの式を使用して次のコードに示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

詳細については、次を参照してください。[明示的なフィールド。`val`キーワード](explicit-fields-the-val-keyword.md)します。

## <a name="executing-side-effects-in-constructors"></a>コンス トラクター内で実行中の副作用

クラスでプライマリ コンス トラクター内のコードを実行できる、`do`バインドします。 ただし、ある場合は、追加のコンス トラクターでないコードを実行する、`do`バインドしますか? これを行うには、使用する、`then`キーワード。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

プライマリ コンス トラクターの副作用は引き続き実行します。 そのため、出力は次に示します。

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>コンス トラクター内の自己識別子

他のメンバーでは、各メンバーの定義では、現在のオブジェクトの名前を指定します。 使用して、クラス定義の最初の行で、自己識別子を配置することもできます、`as`キーワードの直後に次のコンス トラクターのパラメーター。 次の例は、この構文を示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

追加のコンス トラクターで定義することも自己識別子を配置することで、`as`直後にコンス トラクターのパラメーターの句。 次の例は、この構文を示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

完全に定義する前に、オブジェクトを使用しようとすると、問題が発生することができます。 そのため、自己識別子の使用は、コンパイラ警告が生成され、オブジェクトが初期化される前に、オブジェクトのメンバーがアクセスされないようにする追加のチェックを挿入するを発生することができます。 自己識別子のみを使用する必要があります、`do`バインドまたは後に、プライマリ コンス トラクターの`then`キーワード コンス トラクターを追加します。

自己識別子の名前がない`this`します。 任意の有効な識別子があります。

## <a name="assigning-values-to-properties-at-initialization"></a>プロパティの初期化時に値を割り当てる

フォームの割り当ての一覧を追加して、初期化コードでクラスのオブジェクトのプロパティに値を割り当てることができます`property = value`コンス トラクターの引数リストにします。 これを次のコード例に示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

前のコードの次のバージョンは、通常の引数、省略可能な引数、および 1 つのコンス トラクターの呼び出しのプロパティの設定の組み合わせを示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>継承されたクラスのコンス トラクター

コンス トラクターを持つ基本クラスを継承する場合は、継承句でその引数を指定する必要があります。 詳細については、[コンス トラクターと継承](../inheritance.md#constructors-and-inheritance)を参照してください。

## <a name="static-constructors-or-type-constructors"></a>静的コンス トラクターまたは型コンス トラクター

静的オブジェクトを作成するためのコードを指定するだけでなく`let`と`do`型レベルでの初期化を実行する型が最初に使用される前に実行するクラス型でバインディングを作成できます。 詳細については、[ `let`クラス内のバインディング](let-bindings-in-classes.md)と[`do`クラス内のバインディング](do-bindings-in-classes.md)を参照してください。

## <a name="see-also"></a>関連項目

- [メンバー](index.md)