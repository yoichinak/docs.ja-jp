---
title: 遅延式
description: 学習方法F#遅延式は、アプリとライブラリのパフォーマンスを向上させることができます。
ms.date: 03/13/2019
ms.openlocfilehash: 6d53d53093f4e93f53e1c956b94e2f1e4a1bbd55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904112"
---
# <a name="lazy-expressions"></a>遅延式

*遅延式*は、すぐには評価されませんが、結果が必要な場合は代わりに評価される式です。 これは、コードのパフォーマンスを向上させるために役立ちます。

## <a name="syntax"></a>構文

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Remarks

前の構文で*式*結果が、必要な場合にのみ評価されるコードと*識別子*は結果を格納する値です。 型の値は、 [ `Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)場所、実際の種類のために使用`'T`式の結果から決定されます。

遅延式を使用すると、結果が必要な場合のみ、式の実行を制限することでパフォーマンスを向上させることができます。

メソッドを呼び出すを強制的に実行する式、`Force`します。 `Force` 1 回だけ実行する実行をします。 後続の呼び出し`Force`同じが、任意のコードを実行せずに返します。

次のコードは限定的な表現の使用と、使用して`Force`します。 このコードの種類で`result`は`Lazy<int>`、および`Force`メソッドを返します。、`int`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

遅延評価は、ではなく、`Lazy`入力、シーケンスにも使用します。 詳細については、次を参照してください。[シーケンス](sequences.md)します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [LazyExtensions モジュール](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
