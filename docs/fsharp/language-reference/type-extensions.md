---
title: 型拡張
description: 学習方法F#型の拡張機能により、定義済みのオブジェクト型に新しいメンバーを追加します。
ms.date: 02/08/2019
ms.openlocfilehash: 69fb3b771b5334c5771f2ac75341b38c1dad5b90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982606"
---
# <a name="type-extensions"></a>型の拡張機能

拡張機能を入力 (とも呼ばれる_拡張_) は、以前に定義されたオブジェクト型に新しいメンバーを追加する機能のファミリです。 3 つの機能は次のとおりです。

* 組み込み型拡張
* 省略可能な型の拡張機能
* 拡張メソッド

それぞれ異なるシナリオで使用できるあり、さまざまなトレードオフです。

## <a name="syntax"></a>構文

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a>組み込み型拡張

組み込み型拡張機能とは、ユーザー定義型を拡張する型の拡張機能です。

組み込み型拡張を同じファイルで定義する必要があります**と**で同じ名前空間またはモジュールを展開している、型として。 その他の任意の定義が発生している[オプション型拡張](type-extensions.md#optional-type-extensions)。

組み込み型拡張機能は、機能型の宣言から分離する使うがよい場合があります。 次の例では、組み込み型拡張機能を定義する方法を示します。

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

型拡張機能を使用すると、それぞれを次のことができます。

* 宣言を`Variant`型
* 印刷する機能、`Variant`の「形状」によってクラス
* オブジェクト スタイルの印刷機能にアクセスする手段`.`の表記

これの代わりにすべてのメンバーとして定義するのには、`Variant`します。 本質的に優れたアプローチではありませんが、一部の状況で機能のより明確な表現になります。

組み込み型拡張機能が強化され、型がリフレクションによって調べられると、型に表示されますが、型のメンバーとしてコンパイルされます。

## <a name="optional-type-extensions"></a>省略可能な型の拡張機能

省略可能な型の拡張機能は、元のモジュール、名前空間、または拡張する型のアセンブリの外側に表示される拡張機能です。

省略可能な型の拡張機能は、自分で定義していない種類の拡張に役立ちます。 例:

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

今すぐアクセスすることができます`RepeatElements`のメンバーである場合、<xref:System.Collections.Generic.IEnumerable%601>限り、`Extensions`モジュールはで作業しているスコープで開かれます。

省略可能な拡張機能は、リフレクションして調べる場合は、拡張型には表示されません。 省略可能な拡張機能は、モジュールである必要がありますあり、スコープ内でのみ、拡張機能を含むモジュールが開いているか、それ以外の場合は、スコープ内で場合です。

任意拡張のメンバーはコンパイルされると、静的メンバーになります。このメンバーに対する最初のパラメーターとして、オブジェクト インスタンスが暗黙で渡されます。 ただし、インスタンス メンバーまたはそれらの宣言方法に従って、静的メンバーである場合に機能します。

省略可能な拡張メンバーもに表示されないC#または VB のコンシューマーです。 他でのみ利用F#コード。

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>組み込みと省略可能な型の拡張機能の一般的な制限

型の変数が制限されるジェネリック型の型の拡張機能を宣言することになります。 要件は、拡張機能の宣言の制約が宣言された型の制約と一致することです。

ただし、宣言された型と型の拡張機能の間の制約に一致した場合でも、宣言された型よりも、型パラメーターに異なる要件を適用する拡張メンバーの本文で推測に、制約の可能なは。 例:

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

省略可能な型の拡張機能を使用するには、このコードを取得する方法はありません。

* `Sum`メンバーは、さまざまな制約に`'T`(`static member get_Zero`と`static member (+)`) よりの種類の拡張子で定義されています。
* 変更の種類の拡張子として同じ制約が`Sum`で定義された制約に一致が不要になった`IEnumerable<'T>`します。
* 変更する`member this.Sum`に`member inline this.Sum`はエラーの種類の制約が一致しないことになります。

何が必要なは、"領域で float"と、これらの種類の拡張しているかのように表示されることができますを静的メソッドです。 これは、拡張メソッドが必要になります。

## <a name="extension-methods"></a>拡張メソッド

最後に、(「C# スタイル拡張メンバー」とも呼ばれます) の拡張メソッドは、クラスのプロセスのメンバーが静的メソッドとして F# で宣言できます。

拡張メソッドは、型の変数を制約するジェネリック型で拡張を定義するときに役立ちます。 例:

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

使用すると、このコードが表示されるようにまるで`Sum`で定義された<xref:System.Collections.Generic.IEnumerable%601>限り、`Extensions`が開かれているかがスコープ内にします。

## <a name="other-remarks"></a>その他のコメント

型の拡張機能では、次の属性もあります。

* アクセスできる任意の型を拡張できます。
* 組み込みと省略可能な型の拡張機能を定義できます_任意_メンバーの種類、だけでなくメソッド。 拡張機能プロパティは、例では可能であればもします。
* `self-identifier`トークンで、[構文](type-extensions.md#syntax)通常のメンバーと同じように、呼び出される型のインスタンスを表します。
* 拡張メンバーは、静的またはインスタンス メンバーです。
* 型の変数型の拡張機能には、宣言型の制約に一致する必要があります。

型の拡張機能も、次の制限があります。

* 型の拡張機能は、仮想または抽象メソッドをサポートしていません。
* 型の拡張機能では、拡張としてオーバーライド メソッドをサポートしていません。
* 型の拡張機能をサポートしていない[Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md)します。
* 省略可能な型の拡張機能では、拡張としてのコンス トラクターはサポートされません。
* 型の拡張機能では定義できません[省略名を入力](type-abbreviations.md)します。
* 型の拡張機能は無効な`byref<'T>`(ただし、これらを宣言することができます)。
* 型の拡張機能は、(ただし、これらを宣言することができます)、属性は無効です。
* 同じ名前の他のメソッドをオーバー ロードする拡張機能を定義することができますが、F# コンパイラでは、あいまいな呼び出しがある場合は非拡張メソッドを優先します。

最後に、1 つの型に対して複数の組み込み型拡張が存在する場合は、すべてのメンバーが一意である必要があります。 オプション型拡張の場合は、1 つの型に対する複数の型拡張が存在する場合でも、各メンバーに同じ名前を付けることができます。 クライアント コードで同じメンバー名が定義されている 2 つの異なるスコープを開いている場合にのみ、あいまいさに対するエラーが発生します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [メンバー](members/index.md)
