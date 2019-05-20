---
title: sizeof - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 8bb6d4a37b2eea3060921937cf15a1fdd1be97b4
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634006"
---
# <a name="sizeof-c-reference"></a>sizeof (C# リファレンス)

アンマネージ型のサイズ (バイト単位) を取得するときに使用します。

アンマネージド型には次のようなものがあります。

- 次の表は単純型の一覧です。

   |正規表現|定数値|
   |----------------|--------------------|
   |`sizeof(sbyte)`|1|
   |`sizeof(byte)`|1|
   |`sizeof(short)`|2|
   |`sizeof(ushort)`|2|
   |`sizeof(int)`|4|
   |`sizeof(uint)`|4|
   |`sizeof(long)`|8|
   |`sizeof(ulong)`|8|
   |`sizeof(char)`|2 (Unicode)|
   |`sizeof(float)`|4|
   |`sizeof(double)`|8|
   |`sizeof(decimal)`|16|
   |`sizeof(bool)`|1|

- 列挙型。

- ポインター型。

- 参照型または構築された型である任意のインスタンス フィールドまたは自動実装インスタンス プロパティが含まれていないユーザー定義の構造体。

次の例は、`int` のサイズを取得する方法を示しています。

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a>解説

C# のバージョン 2.0 以降、`sizeof` を単純型または列挙型に適用する場合、そのコードを [unsafe](unsafe.md) コンテキストでコンパイルする必要がなくなりました。

`sizeof` 演算子はオーバーロードできません。 `sizeof` 演算子により返される値の型は `int` です。 上記の表に、特定の単純型をオペランドとする `sizeof` 式と、代用される定数値を示します。

struct など、その他の型については、`sizeof` 演算子はアンセーフ コード ブロックでのみ使用できます。 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> メソッドを使用できますが、このメソッドによって返される値は常に `sizeof` によって返される値と同じとは限りません。 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> は、型のマーシャリング後にサイズを返します。一方、`sizeof` は、共通言語ランタイムによって割り当てられたサイズ (埋め込みを含む) を返します。

## <a name="example"></a>例

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [演算子のキーワード](operator-keywords.md)
- [enum](enum.md)
- [アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)
- [構造体](../../programming-guide/classes-and-structs/structs.md)
- [定数](../../programming-guide/classes-and-structs/constants.md)
