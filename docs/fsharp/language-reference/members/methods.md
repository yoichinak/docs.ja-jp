---
title: メソッド
description: 学習方法、F#メソッドは、公開し、オブジェクトと型の動作と機能の実装に使用される型に関連付けられている関数。
ms.date: 05/16/2016
ms.openlocfilehash: 9b661a3ff7fa9a7704f5a31570acb62deaac2fcf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641759"
---
# <a name="methods"></a>メソッド

A*メソッド*型に関連付けられている関数です。 オブジェクト指向のプログラミングで公開し、オブジェクトと型の動作と機能を実装するメソッドを使用します。

## <a name="syntax"></a>構文

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a>Remarks

前の構文では、メソッドの宣言と定義のさまざまなフォームを表示できます。 長いメソッド本体では、改行されるように等号 (=) と、メソッド本体の全体がインデントされます。

属性は、任意のメソッド宣言に適用できます。 メソッド定義の構文の前に、個別の行に、通常は一覧表示されます。 詳細については、「[属性](../attributes.md)」を参照してください。

メソッドをマークする`inline`します。 `inline` の詳細については、「[Inline Functions](../functions/inline-functions.md)」(インライン関数) を参照してください。

非インライン メソッドは、型内で再帰的に使用できます。明示的に使用する必要はありません、`rec`キーワード。

## <a name="instance-methods"></a>インスタンス メソッド

インスタンス メソッドを宣言すると、`member`キーワードと*自己識別子*、その後にピリオド (.) とメソッド名とパラメーター。 場合と同様`let`、バインド、*パラメーター リスト*パターンを指定できます。 通常、他の .NET Framework 言語で作成されるときに、F# の方法は、組の形式でのかっこ内のパラメーターの表示方法を囲みます。 ただし、カリー化された形式 (パラメーターをスペースで区切られた) は一般的でも、その他のパターンもサポートされます。

次の例では、定義とインスタンスの非抽象メソッドの使用方法を示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

インスタンスのメソッド内では、let バインドを使用して定義されているフィールドにアクセスする、自己識別子を使用しないでください。 その他のメンバーとプロパティにアクセスする場合は、自己識別子を使用します。

## <a name="static-methods"></a>静的メソッド

キーワード`static`インスタンスがないメソッドを呼び出すことができますを指定するために使用して、オブジェクトのインスタンスに関連付けられていません。 それ以外の場合、メソッドは、インスタンス メソッドです。

次のセクションの例で宣言されたフィールドを示しています、`let`キーワード、プロパティのメンバーを使って宣言する場合、`member`キーワード、および静的メソッドで宣言された、`static`キーワード。

次の例は、定義と静的メソッドの使用を示しています。 これらのメソッド定義であると仮定、`SomeType`クラスは、前のセクションでします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>抽象メソッドと仮想メソッド

キーワード`abstract`メソッドが仮想ディスパッチ スロットを持つクラスの定義がないことを示します。 A*仮想ディスパッチ スロット*はオブジェクト指向型の仮想関数を検索する実行時に使用される関数の内部で維持されるテーブル内のエントリを呼び出します。 仮想ディスパッチ メカニズムを実装するメカニズムは、*ポリモーフィズム*、オブジェクト指向プログラミングの重要な機能です。 定義のない 1 つ以上の抽象メソッドを持つクラスは、*抽象クラス*、つまり、そのクラスのインスタンスを作成できないことができます。 抽象クラスの詳細については、次を参照してください。[抽象クラス](../abstract-classes.md)します。

抽象メソッドの宣言では、メソッド本体は含まれません。 代わりに、メソッドの名前は後にコロン (:) と、メソッドの型シグネチャ。 メソッドの型のシグネチャは、一時停止すると、マウス ポインター経由での Visual Studio コード エディターでメソッドの名前を除くパラメーターの名前のない、IntelliSense によって表示されるのと同じ。 型のシグネチャは、対話形式で作業している場合にも、インタープリター fsi.exe をで表示されます。 戻り値の型の適切な区切り記号の後に、パラメーターの型を一覧することにより、メソッドの型シグネチャが形成されます。 カリー化されたパラメーターを指定する`->`タプルのパラメーターを指定して`*`します。 戻り値がによって引数から常に区切られた、`->`シンボル。 かっこは、パラメーター、関数型の場合など、複雑なパラメーターをグループ化するかを示すタプルが扱われると、2 つのパラメーターとしてではなく、1 つのパラメーターとして使用できます。

与えることができますも抽象メソッド default 定義、クラスを定義を追加しを使用して、`default`キーワードは、このトピックの「構文のブロックに示されました。 同じクラスの定義を持つ抽象メソッドは、他の .NET Framework 言語での仮想メソッドと同じです。 定義が存在するかどうか、`abstract`キーワードは、クラスの仮想関数テーブルに新しいディスパッチ スロットを作成します。

派生クラスは基底クラスが抽象メソッドを実装するかどうかに関係なく、抽象メソッドの実装を提供できます。 使用してを除く、派生クラスで、同じ名前とシグネチャを持つメソッドを定義する派生クラスで抽象メソッドを実装するために、`override`または`default`キーワード、メソッド本体を提供します。 キーワード`override`と`default`まったく同じことを意味します。 使用して、`override`新しいメソッドは、基本クラス実装をオーバーライドする場合を使用して、`default`は元の抽象宣言と同じクラスで実装を作成するとします。 使用しないでください、`abstract`抽象基本クラスで宣言されたメソッドを実装するメソッドのキーワード。

次の例は、抽象メソッドを示しています。`Rotate`を持つ既定の実装では、.NET Framework の仮想メソッドに相当します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

次の例は、基底クラス メソッドをオーバーライドする派生クラスを示しています。 この場合、オーバーライドでは、何も実行するために、動作が変わります。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>オーバーロードされたメソッド

オーバー ロードされたメソッドは、特定の型で同じ名前があるが、異なる引数を指定する方法です。 F#、省略可能な引数は、通常、オーバー ロードされたメソッドの代わりに使用します。 ただし、オーバー ロードされたメソッドは、されるとき、引数が、組形式いないカリー化された形式では、言語では、許可されます。

## <a name="optional-arguments"></a>省略可能な引数

以降でF#4.1、メソッドで、既定パラメーター値は省略可能な引数を用意することもできます。  これは、c# コードとの相互運用の促進を支援します。  次の例では、構文を示しています。

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

値が渡されたメモ`DefaultParameterValue`入力の型に一致する必要があります。  上記のサンプルでは、`int`します。  整数以外の値を渡そうとした`DefaultParameterValue`コンパイル エラーになります。

## <a name="example-properties-and-methods"></a>例:プロパティとメソッド

次の例には、フィールド、プライベート関数、プロパティ、および静的メソッドの例を紹介する型が含まれています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>関連項目

- [メンバー](index.md)
