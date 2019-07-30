---
title: 'インポート宣言: open キーワード'
description: 完全修飾名を使用せずに参照できる要素を持つ F# インポート宣言し、モジュールまたは名前空間の指定方法について説明します。
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630574"
---
# <a name="import-declarations-the-open-keyword"></a>インポート宣言: `open` キーワード

> [!NOTE]
> この記事の API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

*インポート宣言*は、完全修飾名を使用せずに参照できる要素を持つモジュールまたは名前空間を指定します。

## <a name="syntax"></a>構文

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Remarks

常に完全修飾名前空間またはモジュールパスを使用してコードを参照すると、書き込み、読み取り、および保守が困難なコードを作成できます。 代わりに、頻繁に使用さ`open`れるモジュールと名前空間にキーワードを使用して、そのモジュールまたは名前空間のメンバーを参照するときに、完全修飾名の代わりに短い形式の名前を使用できます。 このキーワードはC#、 `using namespace`のキーワード`using` 、ビジュアルC++、および Visual Basic に似`Imports`ています。

指定されたモジュールまたは名前空間は、同じプロジェクトまたは参照されるプロジェクトまたはアセンブリ内に存在する必要があります。 そうでない場合は、プロジェクトへの参照を追加するか、 `-reference`コマンド`-`ラインオプション`-r`(またはその省略形) を使用することができます。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。

インポート宣言は、外側の名前空間、モジュール、またはファイルの末尾まで、宣言の後のコードで名前を使用できるようにします。

複数のインポート宣言を使用する場合は、別々の行に表示する必要があります。

次のコードは、 `open`キーワードを使用してコードを簡略化する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

複数F#の開いているモジュールまたは名前空間で同じ名前が発生した場合に、あいまいさが発生すると、コンパイラはエラーまたは警告を生成しません。 あいまいさが発生すると、F# より最近開いたモジュールまたは名前空間を設定できます。 たとえば、次の`empty`コードでは、 `List`と`Seq.empty` `Seq`の両方の`empty`モジュールにがある場合でも、はを意味します。

```fsharp
open List
open Seq
printfn "%A" empty
```

したがって、同じ名前を持つメンバーが含まれて`List` `Seq`いるモジュールまたは名前空間を開く場合は注意が必要です。代わりに、修飾名の使用を検討してください。 コードがインポート宣言の順序に依存している状況を避ける必要があります。

## <a name="namespaces-that-are-open-by-default"></a>既定で開かれている名前空間

一部の名前空間は、これらの明示的なインポート宣言は必要ありませんが暗黙的に開かれた F# コードで頻繁に使用されます。 次の表は、既定で開かれている名前空間を示しています。

|名前空間|説明|
|---------|-----------|
|`Microsoft.FSharp.Core`|基本的な F# の型定義の組み込み型を含む`int`と`float`します。|
|`Microsoft.FSharp.Core.Operators`|`+` や`*`などの基本的な算術演算が含まれています。|
|`Microsoft.FSharp.Collections`|`List` や`Array`などの変更できないコレクションクラスが含まれています。|
|`Microsoft.FSharp.Control`|レイジー評価や非同期ワークフローなどのコントロール構成要素の型が含まれています。|
|`Microsoft.FSharp.Text`|関数など、書式設定された`printf` IO 用の関数が含まれています。|

## <a name="autoopen-attribute"></a>AutoOpen 属性

アセンブリが参照さ`AutoOpen`れたときに名前空間またはモジュールを自動的に開く場合は、アセンブリに属性を適用できます。 また、 `AutoOpen`属性をモジュールに適用して、親モジュールまたは名前空間を開いたときに自動的にそのモジュールを開くようにすることもできます。 詳細については、「 [Core. AutoOpenAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)」を参照してください。

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess 属性

一部のモジュール、レコード、または共用体型で`RequireQualifiedAccess`は、属性を指定できます。 これらのモジュール、レコード、または共用体の要素を参照する場合は、インポート宣言を含めるかどうかに関係なく、修飾名を使用する必要があります。 一般的に使用される名前を定義する型でこの属性を戦略的に使用すると、名前の競合を避けることができるため、ライブラリの変更に対するコードの回復性が向上します。 詳細については、「 [RequireQualifiedAccessAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [名前空間](namespaces.md)
- [モジュール](modules.md)
