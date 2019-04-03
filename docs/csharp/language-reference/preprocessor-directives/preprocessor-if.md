---
title: '#if プリプロセッサ ディレクティブ - C# リファレンス'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: b92660a69194ff2d52cd78427f73510de514ea48
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545820"
---
# <a name="if-c-reference"></a>#if (C# リファレンス)

C# コンパイラでは、`#if` ディレクティブ、次いで [#endif](preprocessor-endif.md) ディレクティブが検出されると、これらのディレクティブ間のコードがコンパイルされます (指定されたシンボルが定義されている場合に限る)。 C および C++ とは異なり、シンボルに数値を割り当てることはできません。 C# の #if ステートメントはブール値で、シンボルが定義されているかどうかのみをテストします。 次に例を示します。

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

[==](../operators/equality-operators.md#equality-operator-) (等しい) および [!=](../operators/equality-operators.md#inequality-operator-) (等しくない) の各演算子は、[true](../keywords/true.md) か [false](../keywords/false.md) のどちらであるかのテストにのみ使用できます。 true は、シンボルが定義されていることを意味します。 ステートメント `#if DEBUG` と `#if (DEBUG == true)` の意味は同じです。 [&&](../operators/conditional-and-operator.md) (かつ)、[&#124;&#124;](../operators/conditional-or-operator.md) (または)、および [!](../operators/logical-negation-operator.md) (not) の各演算子を使用すると、複数のシンボルが定義されているかどうかを評価できます。 シンボルと演算子は、かっこを使用してグループ化できます。

## <a name="remarks"></a>解説

`#if` と [#else](preprocessor-else.md)、[#elif](preprocessor-elif.md)、[#endif](preprocessor-endif.md)、[#define](preprocessor-define.md)、[#undef](preprocessor-undef.md) の各ディレクティブを組み合わせると、1 つ以上のシンボルが存在するかどうかに応じてコードを含めたり除外したりできます。 これは、デバッグ ビルドのコードをコンパイルする場合や、特定の構成でコンパイルを行う場合に役立ちます。

`#if` ディレクティブで始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了させる必要があります。

`#define` を使用するとシンボルを定義できます。 定義したシンボルを `#if` ディレクティブに渡す式として使用すると、この式は `true` と評価されます。

シンボルは、[-define](../compiler-options/define-compiler-option.md) コンパイラ オプションでも定義できます。 [#undef](preprocessor-undef.md) を使うと、シンボルを未定義状態にできます。

`-define` または `#define` で定義されたシンボルは、同じ名前の変数とは競合しません。 変数名をプリプロセッサ ディレクティブに渡すことはできません。シンボルはプリプロセッサ ディレクティブだけで評価されます。

`#define` を使用して作成したシンボルのスコープは、そのシンボルが定義されているファイルです。

また、ビルド システムも、各種[ターゲット フレームワーク](../../../standard/frameworks.md)を表す、定義済みプリプロセッサ シンボルを認識します。 これは、複数の .NET の実装やバージョンをターゲットとできるアプリケーションを作成する場合に役立ちます。

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

他の定義済みシンボルとしては、DEBUG 定数と TRACE 定数があります。 `#define` を使用して、プロジェクトに設定された値をオーバーライドできます。 たとえば、DEBUG シンボルは、ビルド構成プロパティ ("デバッグ" モードまたは "リリース" モード) に応じて自動的に設定されます。

## <a name="examples"></a>使用例

次の例は、ファイルで MYTEST シンボルを定義し、MYTEST シンボルと DEBUG シンボルの値をテストする方法を示しています。 この例の出力は、プロジェクトをデバッグとリリースのどちらの構成モードでビルドするかによって異なります。

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

次の例は、各種ターゲット フレームワークをテストし、可能な場合には新しい API を使用できるようにする方法を示しています。

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a>関連項目

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](index.md)
- [方法: トレースとデバッグを指定して条件付きコンパイルを実行する](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
