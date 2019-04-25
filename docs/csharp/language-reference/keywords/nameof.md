---
title: nameof - C# リファレンス
ms.custom: seodec18
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 04de4dc6f320213c1a9c95b1abb92488fac0a81f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614091"
---
# <a name="nameof-c-reference"></a>nameof (C# リファレンス)

変数、型、またはメンバーの単純な (修飾されていない) 文字列名を取得するのに使用します。

コード内のエラーの報告、モデル ビュー コントローラー (MVC) リンクのフック、プロパティの変更されたイベントの起動などの際には、多くの場合、メソッドの文字列名をキャプチャします。  `nameof` の使用は、定義の名前を変更するときに、コードを有効な状態に保つのに役立ちます。  以前は、定義を参照するのに文字列リテラルを使用する必要がありました。ツールには、これらの文字列リテラルを検査する方法がわからないため、コード要素の名前変更の際には当てになりません。

`nameof` 式のフォームは次のとおりです。

```csharp
if (x == null) throw new ArgumentNullException(nameof(x));
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"
```

## <a name="key-use-cases"></a>主なユース ケース

ここでは、`nameof` の主なユース ケースを示します。

パラメーターの確認:

 ```csharp
void f(string s) {
    if (s == null) throw new ArgumentNullException(nameof(s));
}
```

MVC アクション リンク:

```html
<%= Html.ActionLink("Sign up",
             @typeof(UserController),
             @nameof(UserController.SignUp))
%>
```

INotifyPropertyChanged:

```csharp
int p {
    get { return this.p; }
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too
}
```

XAML 依存関係プロパティ:

```csharp
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));
```

ログ:

```csharp
void f(int i) {
    Log(nameof(f), "method entry");
}
```

属性:

```csharp
[DebuggerDisplay("={" + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

## <a name="examples"></a>使用例

ここでは、C# の例をいくつか示します。

```csharp
using Stuff = Some.Cool.Functionality
class C {
    static int Method1 (string x, int y) {}
    static int Method1 (string x, string y) {}
    int Method2 (int z) {}
    string f<T>() => nameof(T);
}

var c = new C()

class Test {
    static void Main (string[] args) {
        Console.WriteLine(nameof(C)); // -> "C"
        Console.WriteLine(nameof(C.Method1)); // -> "Method1"
        Console.WriteLine(nameof(C.Method2)); // -> "Method2"
        Console.WriteLine(nameof(c.Method1)); // -> "Method1"
        Console.WriteLine(nameof(c.Method2)); // -> "Method2"
        // Console.WriteLine(nameof(z)); -> "z" [inside of Method2 ok, inside Method1 is a compiler error]
        Console.WriteLine(nameof(Stuff)); // -> "Stuff"
        // Console.WriteLine(nameof(T)); -> "T" [works inside of method but not in attributes on the method]
        Console.WriteLine(nameof(f)); // -> "f"
        // Console.WriteLine(nameof(f<T>)); -> [syntax error]
        // Console.WriteLine(nameof(f<>)); -> [syntax error]
        // Console.WriteLine(nameof(Method2())); -> [error "This expression does not have a name"]
    }
}
```

## <a name="remarks"></a>解説

`nameof` への引数は、簡易名、修飾名、メンバー アクセス、メンバーを指定した base アクセス、またはメンバーを指定した this アクセスでなければなりません。  引数の式はコード定義を識別しますが、評価されることはありません。

引数は構文上、式でなければならないため、許容されないものが多数あります。特に必要がないため、ここではこのようなものについて逐一取り上げていません。  定義済みの型 (たとえば、`int` または `void`)、Null 許容型 (`Point?`)、配列型 (`Customer[,]`)、ポインター型 (`Buffer*`)、修飾されたエイリアス (`A::B`)、バインドされていないジェネリック型 (`Dictionary<,>`)、プリプロセッサ シンボル (`DEBUG`)、およびラベル (`loop:`) はエラーが発生するため、注意が必要です。

完全修飾名を取得する必要がある場合は、`nameof` と共に `typeof` 式を使用できます。  次に例を示します。

```csharp
class C {
    void f(int i) {
        Log($"{typeof(C)}.{nameof(f)}", "method entry");
    }
}
```

残念ながら、`typeof` は `nameof` のような定数式ではないので、`nameof` が使われるすべての場所で `nameof` と組み合わせて `typeof` を使うことはできません。  たとえば、次のコードでは CS0182 コンパイル エラーが発生します。

```csharp
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

上記の例では、型名を使用でき、インスタンス メソッド名にアクセスできることが分かります。  評価された式で必要とされるような、型のインスタンスは必要ありません。  型名の使用は状況によっては非常に便利です。型名では名前を参照しているだけでインスタンス データを使用してはいないため、インスタンス変数や式を考慮する必要はありません。

クラスの属性式内でクラスのメンバーを参照できます。

"`Method1 (str, str)`" などの署名情報を取得する方法はありません。  そうする 1 つの方法は、`Expression e = () => A.B.Method1("s1", "s2")` という式を使用し、結果として得られる式ツリーから MemberInfo を取得することです。

## <a name="language-specifications"></a>言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の [nameof 演算子](~/_csharplang/spec/expressions.md#nameof-expressions)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [typeof](../../../csharp/language-reference/keywords/typeof.md)
