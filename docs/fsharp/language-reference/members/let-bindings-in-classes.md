---
title: クラス内の let 束縛
description: クラス定義で 'let' のバインドを使用して、プライベート フィールドと F# クラスのプライベート関数を定義する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 29f843e3e065837a53fd5eb26c79088bc0778c76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645183"
---
# <a name="let-bindings-in-classes"></a>クラス内の let バインド

使用して、プライベート フィールドと F# クラスのプライベート関数を定義することができます`let`クラス定義にバインドします。

## <a name="syntax"></a>構文

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Remarks

クラスの見出しと継承宣言後、メンバーの定義の前に、前の構文が表示されます。 ような構文は、`let`クラスがクラスで定義した名前の外部でバインドがクラスに限定されているスコープを設定します。 A`let`バインディングは、プライベート フィールドまたはデータを公開する関数を作成します。 または、関数で公開されている、プロパティまたはメンバー メソッドを宣言します。

A`let`バインドがない静的なインスタンスと呼びます`let`バインドします。 インスタンス`let`バインド オブジェクトが作成されたときに実行します。 静的`let`バインド型が最初に使用される前に実行することが保証されると、クラスの静的初期化子の一部であります。

インスタンス内のコード`let`バインドは、プライマリ コンス トラクターのパラメーターを使用できます。

属性およびアクセシビリティ修飾子がで許可されていません`let`クラスにバインドします。

次のコード例は、いくつかの種類を示しています`let`クラスにバインドします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

出力は次のとおりです。

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>フィールドを作成する別の方法

使用することも、`val`プライベート フィールドを作成するキーワード。 使用する場合、`val`キーワードが与えられていない値と、オブジェクトが作成されますが、代わりに、既定値で初期化されます。 詳細については、次を参照してください。[明示的なフィールド:Val キーワード](explicit-fields-the-val-keyword.md)します。

メンバーの定義を使用して、キーワードを追加して、クラスでプライベート フィールドを定義することもできます`private`を定義します。 コードを書き直すことがなく、メンバーのアクセシビリティを変更する場合に便利なことができます。 詳細については、「[Access Control](../access-control.md)」(アクセス制御) を参照してください。

## <a name="see-also"></a>関連項目

- [メンバー](index.md)
- [クラス内の `do` バインド](do-bindings-in-classes.md)
- [`let` バインド](../functions/let-bindings.md)
