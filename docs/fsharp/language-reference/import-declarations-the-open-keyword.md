---
title: インポート宣言:Open キーワード
description: 完全修飾名を使用せずに参照できる要素を持つ F# インポート宣言し、モジュールまたは名前空間の指定方法について説明します。
ms.date: 04/04/2019
ms.openlocfilehash: ad64190c3243c57a185f3b864270fca80590f079
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055002"
---
# <a name="import-declarations-the-open-keyword"></a>インポート宣言:`open`キーワード

> [!NOTE]
> この記事の API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

*インポート宣言*モジュールまたは名前空間完全修飾名を使用せずに参照できる要素を指定します。

## <a name="syntax"></a>構文

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Remarks

名前空間またはモジュールの完全修飾パスを使用してコードを参照するたびには、書き込み、読み取り、および管理するが難しいコードを作成できます。 代わりに、使用、`open`キーワードのモジュールや名前空間をそのモジュールまたは名前空間のメンバーを参照する場合は、完全修飾名ではなく、名前の短い形式を使用できるように頻繁に使用します。 このキーワードと似ています、 `using` c# でキーワード`using namespace`の Visual c と`Imports`Visual Basic でします。

モジュールまたは指定された名前空間は、同じプロジェクト内、または参照されるプロジェクトまたはアセンブリである必要があります。 そうでない場合は、プロジェクトへの参照を追加またはを使用して、`-reference`コマンド`-`ライン オプション (またはその省略形、 `-r`)。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。

インポート宣言は、それを囲む名前空間、モジュール、またはファイルの最後までの宣言を次のコードで使用可能な名前を使用します。

複数のインポート宣言を使用する場合は、別の行に表示されます。

次のコードは、使用、`open`キーワードをコードを簡略化します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F# 、同じ名前が 1 つ以上の開いているモジュールまたは名前空間で発生すると、あいまいさが発生した場合、コンパイラにエラーまたは警告を同時に生成することはできません。 あいまいさが発生すると、F# より最近開いたモジュールまたは名前空間を設定できます。 たとえば、次のコードで`empty`意味`Seq.empty`場合でも、`empty`両方である、`List`と`Seq`モジュール。

```fsharp
open List
open Seq
printfn "%A" empty
```

そのため、注意を開くときのモジュールまたは名前空間など`List`または`Seq`を含むメンバーの名前は同じでは、代わりに、修飾名の使用を検討してください。 コードのインポート宣言の順序に依存するすべての状況を避ける必要があります。

## <a name="namespaces-that-are-open-by-default"></a>既定で開かれている名前空間

一部の名前空間は、これらの明示的なインポート宣言は必要ありませんが暗黙的に開かれた F# コードで頻繁に使用されます。 次の表では、既定で開かれている名前空間を示します。

|名前空間|説明|
|---------|-----------|
|`Microsoft.FSharp.Core`|基本的な F# の型定義の組み込み型を含む`int`と`float`します。|
|`Microsoft.FSharp.Core.Operators`|基本的な算術演算を含む`+`と`*`します。|
|`Microsoft.FSharp.Collections`|変更できないコレクション クラスを含む`List`と`Array`します。|
|`Microsoft.FSharp.Control`|レイジー評価と非同期ワークフローなどのコントロール構成要素の型が含まれています。|
|`Microsoft.FSharp.Text`|などの書式設定された IO は、関数を含む、`printf`関数。|

## <a name="autoopen-attribute"></a>AutoOpen 属性

適用することができます、`AutoOpen`アセンブリに属性をアセンブリが参照されている場合に、名前空間またはモジュールが自動的に開きたい場合。 適用することも、`AutoOpen`親モジュールまたは名前空間が開かれるときに、そのモジュールを自動的に開くモジュールに属性します。 詳細については、次を参照してください。 [Core.AutoOpenAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)します。

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess 属性

一部のモジュール、レコード、または共用体の型を指定できます、`RequireQualifiedAccess`属性。 これらのモジュール、レコード、または共用体の要素を参照する場合は、インポート宣言を含めるかどうかに関係なく、修飾名を使用する必要があります。 この属性を戦略的に使用する場合は、よくを定義する型名を使用する、役立つように名前の競合を回避し、コードより回復力のあるライブラリの変更に。 詳細については、次を参照してください。 [Core.RequireQualifiedAccessAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [名前空間](namespaces.md)
- [モジュール](modules.md)
