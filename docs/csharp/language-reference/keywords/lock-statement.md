---
title: lock ステートメント - C# リファレンス
ms.custom: seodec18
description: C# lock ステートメントを使用し、共有リソースへのスレッド アクセスを同期します
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: c7d5d4ef7d812e186813cd08f9e4e2adf2ab1a58
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306653"
---
# <a name="lock-statement-c-reference"></a>lock ステートメント (C# リファレンス)

`lock` ステートメントは、指定のオブジェクトに対する相互排他ロックを取得し、ステートメント ブロックを実行してからロックを解放します。 ロックが保持されている間、ロックを保持するスレッドではロックを再度取得し、解放することができます。 他のスレッドはブロックされてロックを取得できず、ロックが解放されるまで待機します。

`lock` ステートメントの形式は次のようになります。

```csharp
lock (x)
{
    // Your code...
}
```

`x` は[参照型](reference-types.md)の式です。 これは次にまったく等しくなります。

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

このコードでは [try...finally](try-finally.md) ブロックが使用されているため、`lock` ステートメントの本文内で例外がスローされた場合でもロックは解放されます。

`lock` ステートメントの本体で [await](await.md) キーワードを使用することはできません。

## <a name="remarks"></a>コメント

共有リソースへのスレッド アクセスを同期する場合、専用オブジェクト インスタンス (`private readonly object balanceLock = new object();` など) またはコードの関連のない部分によってロック オブジェクトとして使用される可能性がない別のインスタンスをロックします。 異なる共有リソースに対して同じロック オブジェクト インスタンスを使用することは避けてください。デッドロックやロックの競合が発生する可能性があります。 特に、以下をロック オブジェクトとして使用しないでください。

- `this`。ロックとして呼び出し元に使用される可能性があります。
- <xref:System.Type> インスタンス。[typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) 演算子またはリフレクションによって取得される可能性があります。
- 文字列リテラルを含む文字列インスタンス。[インターン処理](/dotnet/api/system.string.intern#remarks)される可能性があります。

## <a name="example"></a>例

次の例では、専用 `balanceLock` インスタンスをロックすることでそのプライベート `balance` フィールドへのアクセスを同期する `Account` クラスが定義されます。 ロッキングに同じインスタンスを使用すると、2 つのスレッドが `Debit` または `Credit` メソッドを同時に呼び出すことによって `balance` フィールドを同時に更新することができなくなります。

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C# リファレンス](../index.md)
- [C# のキーワード](index.md)
- [ステートメントのキーワード](statement-keywords.md)
- [同期プリミティブの概要](../../../standard/threading/overview-of-synchronization-primitives.md)
