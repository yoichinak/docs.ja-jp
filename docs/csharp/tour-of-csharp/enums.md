---
title: C# の列挙型 - C# 言語のツアー
description: C# における列挙型、離散した名前付き定数について
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 8c1c29c3c06829da81a9c9be8bb5bd99f1c9e395
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2019
ms.locfileid: "57843125"
---
# <a name="enums"></a>列挙体

***列挙型***は、一連の名前付き定数を使用する固有の値の型です。 一連の離散値が使用される型を定義する必要がある場合に、列挙型を定義します。 列挙型は、整数値の型のいずれかを基になる記憶域として使用します。 列挙型により、離散値にセマンティックな意味が付与されます。

次の例では `Red`、`Green`、および `Blue` の定数 3 つとともに、`Color` と名前付けられた `enum` 型を宣言して使用します。

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

`enum` 型はそれぞれ、`enum` 型の***基になる型***と呼ばれる整数型に対応しています。 基になる型を明示的に宣言しない `enum` 型には `int` の基になる型を持っています。 `enum` 型の記憶域形式と使用可能な値の範囲は基になる方によって決まります。 `enum` 型が処理できる一連の値はその型の `enum` メンバーによって制限されません。 特に、`enum` の基となる型の値はすべて、`enum` 型にキャストされる場合があり、`enum` 型の一意の有効な値です。

次の例では、`Alignment` と名前付けられた `enum` 型を、基となる型 `sbyte` とともに宣言します。

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

前の例のとおり、`enum` メンバーの宣言にはメンバーの値を指定する定数式が含まれる場合があります。 各 `enum` メンバーの定数値は `enum` の基となる型の範囲内にある必要があります。 `enum` メンバーの宣言により値が明示的に指定されない場合、そのメンバーに 0 の値 (`enum` 型の最初のメンバーの場合)、またはテキスト上で先行する `enum` メンバーの値に 1 を足した値が与えられます。

`Enum` の値は型キャストを使用して整数値に変換することができ、その逆方向の変換をすることもできます。 次に例を示します。

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

`enum` 型の既定値はすべて、`enum` 型に変換された 0 の整数値です。 変数が自動的に既定値に初期化された場合、これが `enum` 型の変数に与えられる値です。 `enum` 型の既定値を簡単に利用できるようにするために、リテラルの `0` が任意の `enum` 型に暗黙的に変換されます。 したがって、次の例も許可されます。

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

> [!div class="step-by-step"]
> [前へ](interfaces.md)
> [次へ](delegates.md)
