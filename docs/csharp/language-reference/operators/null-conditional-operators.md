---
title: Null 条件演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 9cbf8a0f860f0bc0328cd98e558b20b5e8e1bf8f
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348844"
---
# <a name="-and--null-conditional-operators-c-reference"></a>?. および ?[] Null 条件演算子 (C# リファレンス)

メンバー アクセス (`?.`) またはインデックス (`?[]`) 操作を実行する前に、左の演算子の値を null に対してテストします。左側のオペランドが `null` に評価される場合、`null` が返されます。

これらの演算子を使用すると、null チェックの処理のために記述するコードを少なくすることができます (特に、データ構造を下っていく場合)。

```csharp
int? length = customers?.Length; // null if customers is null
Customer first = customers?[0];  // null if customers is null
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null
```

Null 条件演算子はショートサーキットです。  条件付きのメンバー アクセスやインデックス操作のチェーンの 1 つの演算が null を返す場合、チェーンの実行の残りの部分は停止します。  次の例では、`A`、`B`、または `C` が null と評価された場合、`E` は実行されません。

```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

null 条件メンバー アクセスの別の用途は、はるかに少ないコードのスレッド セーフな方法でデリゲートを呼び出すことです。  従来の方法には、次のようなコードが必要です。

```csharp
var handler = this.PropertyChanged;
if (handler != null)
    handler(…);
```

新しい方法は格段に単純です。

```csharp
PropertyChanged?.Invoke(…)
```

コンパイラが `PropertyChanged` を評価するためのコードを一度しか生成せず、一時変数に結果が保持されるため、新しい方法はスレッド セーフです。 null 条件デリゲート呼び出し構文 `PropertyChanged?(e)` がないため、`Invoke` メソッドを明示的に呼び出す必要があります。

## <a name="language-specifications"></a>言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の「[Null 条件演算子](~/_csharplang/spec/expressions.md#null-conditional-operator)」をご覧ください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- [?? (Null 合体演算子)](null-coalescing-operator.md)
- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)