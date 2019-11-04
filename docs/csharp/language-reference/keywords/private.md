---
title: private キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 19e2925cd65cc9c68ff50d370398a4f401275940
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422588"
---
# <a name="private-c-reference"></a>private (C# リファレンス)

`private` キーワードはメンバー アクセス修飾子です。

> このページでは、`private` アクセスについて説明します。 `private` キーワードも [`private protected`](./private-protected.md) アクセス修飾子に含まれます。

プライベート アクセスは、最も制限の多いアクセス レベルです。 次の例に示すように、プライベート メンバーは、宣言されているクラスまたは構造体の本体内でのみアクセスできます。

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

同じ本体にある入れ子にされた型も、プライベート メンバーにアクセスできます。

プライベート メンバーへの参照を、クラスの外側やメンバーが宣言されているクラスの外側から行った場合は、コンパイル時のエラーが発生します。

`private` とその他のアクセス修飾子の比較については、「[アクセシビリティ レベル](accessibility-levels.md)」と「[アクセス修飾子](../../programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。

## <a name="example"></a>例

この例では、`Employee` クラスに `name` と `salary` という 2 つのプライベート データ メンバーが含まれています。 これらのメンバーは、プライベート メンバーであり、メンバー メソッド以外からはアクセスできません。 `GetName` と `Salary` というパブリック メソッドが追加されており、プライベート メンバーへの制御されたアクセスが許可されています。 `name` メンバーはパブリック メソッドを通してアクセスされ、`salary` メンバーはパブリックな読み取り専用プロパティを通してアクセスされます (詳細については、「[プロパティ](../../programming-guide/classes-and-structs/properties.md)」を参照してください)。

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>C# 言語仕様  

詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[宣言されたアクセシビリティ](~/_csharplang/spec/basic-concepts.md#declared-accessibility)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [アクセス修飾子](access-modifiers.md)
- [アクセシビリティ レベル](accessibility-levels.md)
- [修飾子](index.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)
