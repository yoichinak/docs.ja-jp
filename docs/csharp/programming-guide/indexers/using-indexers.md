---
title: インデクサーの使用 - C# プログラミング ガイド
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: e742e4dd5ea92ec3baf37c915e024e713022b7b6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416238"
---
# <a name="using-indexers-c-programming-guide"></a>インデクサーの使用 (C# プログラミング ガイド)

インデクサーによって構文上の利便性がもたらされます。これを使用すると、[クラス](../../language-reference/keywords/class.md)、[構造体](../../language-reference/builtin-types/struct.md)、または[インターフェイス](../../language-reference/keywords/interface.md)を作成でき、クライアント アプリケーションから配列と同じようにアクセスできます。 コンパイラによって、`Item` プロパティ (または、<xref:System.Runtime.CompilerServices.IndexerNameAttribute> が存在する場合は別の名前が付けられたプロパティ) と、適切なアクセサー メソッドが生成されます。 インデクサーは、内部コレクションまたは配列をカプセル化することが主な目的である型で最も多く実装されます。 たとえば、24 時間のうちの異なる 10 回の時刻で記録した温度を華氏で表す `TempRecord` クラスがあるとします。 このクラスには、温度値を格納する `float[]` 型の配列 `temps` が含まれています。 このクラスにインデクサーを実装することで、クライアントは、`float temp = tempRecord.temps[4]` ではなく `float temp = tempRecord[4]` として `TempRecord` インスタンスの温度にアクセスできます。 インデクサー表記を使用すると、クライアント アプリケーションの構文が簡略化されるだけでなく、クラスとその目的が、他の開発者たちにとってわかりやすい、より直感的なものとなります。

クラスまたは構造体でインデクサーを宣言するには、次の例のように [this](../../language-reference/keywords/this.md) キーワードを使用します。

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> インデクサーを宣言すると、オブジェクト上に `Item` という名前のプロパティが自動的に生成されます。 `Item` プロパティは、インスタンスの[メンバー アクセス式](../../language-reference/operators/member-access-operators.md#member-access-expression-)から直接アクセスすることはできません。 また、インデクサーを使用して独自の `Item` プロパティをオブジェクトに追加すると、[CS0102 コンパイラエラー](../../misc/cs0102.md)が発生します。 このエラーを回避するには、以下で説明するように、<xref:System.Runtime.CompilerServices.IndexerNameAttribute> を使用してインデクサーの名前を変更します。

## <a name="remarks"></a>Remarks

インデクサーの型とそのパラメーターの型は、少なくとも、インデクサー自体と同程度にアクセス可能である必要があります。 アクセシビリティ レベルの詳細については、「[アクセス修飾子 (C# リファレンス)](../../language-reference/keywords/access-modifiers.md)」を参照してください。

インターフェイスでインデクサーを使用する方法の詳細については、「[インターフェイスのインデクサー (C# プログラミング ガイド)](./indexers-in-interfaces.md)」を参照してください。

インデクサーのシグネチャは、その仮パラメーターの数と型で構成されます。 これには、インデクサーの型や仮パラメーターの名前は含まれません。 同じクラス内に複数のインデクサーを宣言する場合は、異なるシグネチャが必要です。

インデクサーの値は変数として分類されないため、インデクサーの値を [ref](../../language-reference/keywords/ref.md) や [out](../../language-reference/keywords/out-parameter-modifier.md) パラメーターとして渡すことはできません。

他の言語が使用できる名前をインデクサーに指定するには、次の例のように <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType> を使用します。

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

インデクサー名属性によってオーバーライドされるため、このインデクサーの名前は `TheItem` になります。 既定では、インデクサーの名前は `Item` です。

## <a name="example-1"></a>例 1

次の例は、プライベートな配列フィールド `temps` とインデクサーの宣言方法を示しています。 インデクサーを使用すれば、インスタンス `tempRecord[i]` に直接アクセスできます。 インデクサーを使用しない場合は、配列を [public](../../language-reference/keywords/public.md) メンバーとして宣言し、そのメンバー `tempRecord.temps[i]` に直接アクセスします。

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

`Console.Write` ステートメントなどでインデクサーのアクセスが評価されると、[get](../../language-reference/keywords/get.md) アクセサーが呼び出されることに注意してください。 したがって、`get` アクセサーが存在しない場合は、コンパイル時エラーが発生します。

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a>他の値を使用したインデックス作成

C# では、インデクサー パラメーター型は整数に制限されません。 たとえば、文字列をインデクサーで使用すると有効な場合があります。 このようなインデクサーは、コレクション内の文字列を検索し、適切な値を返すことによって実装される場合があります。 アクセサーはオーバーロードできるため、文字列と整数のバージョンは共存できます。

## <a name="example-2"></a>例 2

次の例では、曜日を格納するクラスを宣言しています。 `get` アクセサーは、曜日を示す文字列を受け取り、対応する整数を返します。 たとえば、"Sunday" は 0、"Monday" は 1 などと値を返します。

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a>使用例 2

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a>例 3

次の例では、<xref:System.DayOfWeek?displayProperty=fullName> 列挙型の使用により、曜日を格納するクラスが宣言されています。 曜日を示す `DayOfWeek` が`get` アクセサーにより受け取られ、対応する整数が返されます。 たとえば、`DayOfWeek.Sunday` の場合は 0 が返される、`DayOfWeek.Monday` の場合は 1 が返されるなどです。

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a>使用例 3

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a>信頼性の高いプログラミング

インデクサーのセキュリティと信頼性を改善するには、主に次の 2 つの方法があります。

- クライアント コードが無効なインデックス値を渡しても、それを処理できるように必ずエラー処理戦略を組み込んでください。 このトピックの最初の例の TempRecord クラスには Length プロパティが用意されており、入力がインデクサーに渡される前にクライアント コードで検証できるようになっています。 インデクサー自体にエラー処理コードを配置することもできます。 インデクサーのアクセサー内部でスローされる例外はすべて、ユーザーのために文書化してください。

- [get](../../language-reference/keywords/get.md) および [set](../../language-reference/keywords/set.md) アクセサーのアクセシビリティを設定し、適切な制限を指定します。 これは、`set` アクセサーの場合、特に重要です。 詳細については、「[アクセサーのアクセシビリティの制限](../classes-and-structs/restricting-accessor-accessibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [インデクサー](./index.md)
- [プロパティ](../classes-and-structs/properties.md)
