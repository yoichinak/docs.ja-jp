---
title: ':: 演算子 - C# リファレンス'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 324f6711cdec478e5647b05d84c281f79e95f036
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452363"
---
# <a name="-operator-c-reference"></a>:: 演算子 (C# リファレンス)

名前空間エイリアス修飾子 (`::`) を使用して識別子を検索できます。 この例に示すように、常に 2 つの識別子の間に配置します。

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

`::` 演算子は、"*using 別名ディレクティブ*" と一緒に使用することもできます。

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>解説

名前空間エイリアス修飾子として `global` を指定できます。 これにより、エイリアスを使用した名前空間ではなく、グローバル名前空間で検索が実行されます。

## <a name="for-more-information"></a>詳細情報

`::` 演算子の使用例については、次のセクションを参照してください。

- [方法: グローバル名前空間エイリアスを使用する](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [名前空間キーワード](../keywords/namespace-keywords.md)
- [演算子 .](member-access-operators.md#member-access-operator-)
- [extern エイリアス](../keywords/extern-alias.md)