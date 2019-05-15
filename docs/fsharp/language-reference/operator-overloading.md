---
title: 演算子のオーバーロード
description: クラスまたはレコードの種類と F# でのグローバル レベルで算術演算子をオーバー ロードする方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f4b63818cbdc44d214dca6446162ec9a8922f601
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645360"
---
# <a name="operator-overloading"></a>演算子のオーバーロード

このトピックでは、クラス型またはレコード型の算術演算子をオーバーロードする方法と、グローバル レベルで算術演算子をオーバーロードする方法について説明します。

## <a name="syntax"></a>構文

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Remarks

前の構文で、*演算子記号*の 1 つ`+`、 `-`、 `*`、 `/`、`=`など。 *パラメーター リスト*そのオペレーターの通常の構文で表示される順序でオペランドを指定します。 *メソッド本体*結果の値を構築します。

演算子のオーバーロードには、static を指定する必要があります。 演算子がなどの単項演算子のオーバー ロード`+`と`-`、チルダを使用する必要があります (`~`) で、*演算子記号*いることを示す演算子は、単項演算子および二項演算子ではないのように、次の宣言。

```fsharp
static member (~-) (v : Vector)
```

次のコードは、演算子を 2 つだけ含むベクター クラスを示しています。その 1 つは単項マイナス演算子で、もう 1 つはスカラーによる乗算演算子です。 この例では、ベクターとスカラーの記述順序とは無関係に演算子が機能する必要があるため、必要となるスカラー乗算のオーバーロードは 2 つです。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>新しい演算子の作成

標準演算子はすべてオーバーロードすることができますが、特定の文字を並べて新しい演算子を作成することもできます。 使用できる演算子文字は`!`、 `%`、 `&`、 `*`、 `+`、 `-`、 `.`、 `/`、 `<`、 `=`、 `>`、 `?`、 `@`、 `^`、 `|`、および`~`します。 `~` には、演算子を単項演算子にするという特別な意味があるため、演算子の文字シーケンスに含めることはできません。 すべての演算子には、単項を作成できます。

作成した演算子は、使用した厳密な文字シーケンスに従って、特定の優先順位と結合規則を持つようになります。 結合規則を使用する方向は、左から右にすることも、右から左にすることもできます。シーケンスの中で同じレベルの優先順位を持つ演算子を、かっこを使用せずに記述する場合は、必ず結合規則を使用します。

演算子文字の `.` は、優先順位に影響しません。そのため、通常の乗算演算子と同じ優先順位と結合規則を持つ独自の形式の乗算演算子を定義する場合などに、`.*` のような演算子を作成できます。

演算子のみ`?`と`?<-`で始めることは`?`します。

すべての演算子の優先順位を示すテーブルF#で見つかる[シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)します。

## <a name="overloaded-operator-names"></a>オーバーロードされた演算子の名前

F# コンパイラが演算子の式をコンパイルするときに、その演算子のメソッドが生成されます。このメソッドには、コンパイラにより生成された名前が付けられます。 これは、このメソッドの Microsoft Intermediate Language (MSIL) で使用される名前です。また、リフレクションと IntelliSense でも使用されます。 通常、この名前を F# コードで使用する必要はありません。

次の表に、標準演算子と生成される名前を示します。

|演算子|生成された名前|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

ここに記載されていないその他の演算子文字の組み合わせも演算子として使用できます。その場合の名前は、次の表の各文字の名前を連結して生成されます。 たとえば、+! なります`op_PlusBang`します。

|演算子文字|名前|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a>前置演算子と挿入演算子

*プレフィックス*演算子がオペランドの場合、関数と同様に、または複数のオペランドの前に配置するが必要です。 *"挿入辞"* 演算子が 2 つのオペランドの間で配置する必要があります。

前置演算子として使用できるのは特定の演算子だけです。 演算子は、常に前置演算子であるもの、挿入演算子にも前置演算子にもなるもの、および常に挿入演算子であるものに分けられます。 `!` で始まる演算子 (`!=` を除く) と `~` 演算子、または `~` の繰り返しシーケンスは、常に前置演算子です。 演算子 `+`、`-`、`+.`、`-.`、`&`、`&&`、`%`、および `%%` は、前置演算子にも挿入演算子にもなります。 これらの演算子の前置バージョンを挿入バージョンと区別するには、定義時に前置演算子の先頭に `~` を追加します。 `~` は、演算子の使用時には使用されず、定義時にのみ使用されます。

## <a name="example"></a>例

次のコードは、分数型を実装する際の演算子のオーバーロードの使用例です。 分数は、分子と分母で表されます。 `hcf` 関数を使用して最大公約数を求め、その公約数を使用して約分します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**出力:**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>グローバル レベルの演算子

演算子は、グローバル レベルで定義することもできます。 次のコード定義の演算子`+?`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

上記のコードの出力は `12` になります。

F# のスコープ規則では、新しく定義された演算子が組み込み演算子よりも優先されるため、このようにして、通常の算術演算子を再定義できます。

キーワード `inline` は、グローバル演算子と共に使用されることがよくあります。グローバル演算子は、通常、呼び出し元のコードに適宜組み込まれる小規模関数にします。 演算子関数をインライン化することにより、その関数を静的に解決された型パラメーターと共に使用して、静的に解決されたジェネリック コードを作成することもできます。 詳細については、次を参照してください。[インライン関数](functions/inline-functions.md)と[Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md)します。

## <a name="see-also"></a>関連項目

- [メンバー](members/index.md)
