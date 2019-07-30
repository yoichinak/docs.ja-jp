---
title: 'ループ: while...do 式'
description: しばらくお待ちください...do 式は、指定されたテスト条件が true の間、反復実行 (ループ) を実行するために使用されます。
ms.date: 05/16/2016
ms.openlocfilehash: f05bdd9f8f4b9446d59f68e1231fb75e18e9b526
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630761"
---
# <a name="loops-whiledo-expression"></a>ループ: while...do 式

式`while...do`は、指定されたテスト条件が true の間、反復実行 (ループ) を実行するために使用されます。

## <a name="syntax"></a>構文

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Remarks

*テスト式*が評価されます。その`true`場合、*本体式*が実行され、テスト式が再評価されます。 *本体式*には型`unit`が必要です。 テスト式が`false`の場合、イテレーションは終了します。

次の例は、 `while...do`式の使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

前のコードの出力は、1から20までのランダムな数値のストリームです。最後のバイトは10です。

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> は、シーケンス`while...do`式やその他のコンピュテーション式で使用できます。その場合は、 `while...do`式のカスタマイズされたバージョンが使用されます。 詳細については、「[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [For`for...in`条件](loops-for-in-expression.md)
- [For`for...to`条件](loops-for-to-expression.md)
