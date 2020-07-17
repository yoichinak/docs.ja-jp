---
title: 遅延式
description: レイジー式F#を使用して、アプリとライブラリのパフォーマンスを向上させる方法について説明します。
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630738"
---
# <a name="lazy-expressions"></a>遅延式

*レイジー式*は、すぐに評価されるのではなく、結果が必要になったときに評価される式です。 これは、コードのパフォーマンスを向上させるのに役立ちます。

## <a name="syntax"></a>構文

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Remarks

前の構文では、 *expression*は結果が必要な場合にのみ評価されるコードであり、 *identifier*は結果を格納する値です。 値は型[`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)であり、に`'T`使用される実際の型は、式の結果から決定されます。

レイジー式を使用すると、式の実行を、結果が必要な状況のみに制限することで、パフォーマンスを向上させることができます。

式を強制的に実行するには、メソッド`Force`を呼び出します。 `Force`実行を1回だけ実行します。 後続のを`Force`呼び出すと、同じ結果が返されますが、コードは実行されません。

次のコードは、レイジー式の使用方法との`Force`使用方法を示しています。 このコードで`result`は、の型は`Lazy<int>`で、メソッドは`Force`を返し`int`ます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

遅延評価は、 `Lazy`型ではなく、シーケンスにも使用されます。 詳細については、「[シーケンス](sequences.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [LazyExtensions モジュール](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
