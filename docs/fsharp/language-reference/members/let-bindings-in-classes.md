---
title: クラス内の let 束縛
description: クラス定義で ' let ' バインディングを使用しF#て、クラスのプライベートフィールドとプライベート関数を定義する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216533"
---
# <a name="let-bindings-in-classes"></a>クラス内の let バインド

クラス定義のバインディングを使用F# `let`して、クラスのプライベートフィールドとプライベート関数を定義できます。

## <a name="syntax"></a>構文

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>コメント

前の構文は、クラスの見出しと継承宣言の後、メンバー定義の前に記述されます。 構文は、クラスの外部`let`のバインドの場合と似ていますが、クラスで定義されている名前には、クラスに限定されたスコープがあります。 バインディング`let`は、プライベートフィールドまたは関数を作成します。データまたは関数を公開するには、プロパティまたはメンバーメソッドを宣言します。

静的でない`let` `let`バインディングは、インスタンスバインディングと呼ばれます。 インスタンス`let`バインドは、オブジェクトの作成時に実行されます。 静的`let`バインディングは、クラスの静的初期化子の一部であり、型が最初に使用される前に確実に実行されることが保証されています。

インスタンス`let`バインド内のコードでは、プライマリコンストラクターのパラメーターを使用できます。

属性とアクセシビリティ修飾子は、クラスの`let`バインドでは使用できません。

次のコード例は、クラスの`let`いくつかの種類のバインドを示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

出力は次のとおりです。

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>フィールドを作成する別の方法

また、キーワードを使用`val`してプライベートフィールドを作成することもできます。 `val`キーワードを使用する場合、オブジェクトの作成時にフィールドに値は与えられませんが、代わりに既定値を使用して初期化されます。 詳細については、次を参照してください。[明示的なフィールド:Val キーワード](explicit-fields-the-val-keyword.md)。

メンバー定義を使用し、キーワード`private`を定義に追加することで、クラスのプライベートフィールドを定義することもできます。 これは、コードを書き直さずにメンバーのアクセシビリティを変更することが予想される場合に便利です。 詳細については、[アクセス制御](../access-control.md)を参照してください。

## <a name="see-also"></a>関連項目

- [メンバー](index.md)
- [クラス内の `do` バインド](do-bindings-in-classes.md)
- [`let`現存](../functions/let-bindings.md)
