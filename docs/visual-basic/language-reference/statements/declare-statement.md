---
title: Declare ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: e839fe14c360229fbe0350fd7878c7a844056e8b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005098"
---
# <a name="declare-statement"></a>Declare ステートメント

外部ファイルに実装されているプロシージャへの参照を宣言します。

## <a name="syntax"></a>構文

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ]
' -or-
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]
```

## <a name="parts"></a>指定項目

|項目|定義|
|---|---|
|`attributelist`|任意。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。|
|`accessmodifier`|任意。 次のいずれかになります。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-    の[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br />- [プライベート保護](../../language-reference/modifiers/private-protected.md)<br /><br /> 「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|
|`Shadows`|任意。 「[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)」を参照してください。|
|`charsetmodifier`|任意。 文字セットとファイル検索情報を指定します。 次のいずれかになります。<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) (既定値)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Auto](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|省略可能ですが、`Sub` または `Function` のいずれかが表示されている必要があります。 外部プロシージャが値を返さないことを示します。|
|`Function`|省略可能ですが、`Sub` または `Function` のいずれかが表示されている必要があります。 外部プロシージャが値を返すことを示します。|
|`name`|必須。 この外部参照の名前です。 詳細については、次を参照してください。 [宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)|
|`Lib`|必須。 では、外部プロシージャを含む外部ファイル (DLL またはコードリソース) を識別する `Lib` 句が導入されています。|
|`libname`|必須。 宣言されたプロシージャを含むファイルの名前。|
|`Alias`|任意。 宣言されているプロシージャが、`name` で指定された名前によってファイル内で識別されないことを示します。 @No__t-0 で id を指定します。|
|`aliasname`|@No__t-0 キーワードを使用する場合は必須です。 次の2つの方法のいずれかでプロシージャを識別する文字列。<br /><br /> 引用符で囲まれた、ファイル内のプロシージャのエントリポイント名 (`""`)<br /><br /> \- または -<br /><br /> ファイル内のプロシージャのエントリポイントの序数を指定する整数の後にシャープ記号 (@no__t 0)|
|`parameterlist`|プロシージャがパラメーターを受け取る場合は必須です。 「[パラメーターリスト](../../../visual-basic/language-reference/statements/parameter-list.md)」を参照してください。|
|`returntype`|@No__t-0 が指定され、`Option Strict` が `On` である場合は必須です。 プロシージャによって返される値のデータ型。|

## <a name="remarks"></a>コメント

場合によっては、プロジェクト外のファイル (DLL やコードリソースなど) で定義されたプロシージャを呼び出す必要があります。 この場合、プロシージャが配置されている場所、その識別方法、呼び出し元のシーケンスと戻り値の型、および使用する文字列文字セットなど、プロシージャを正しく呼び出すために必要な情報には、Visual Basic コンパイラがアクセスできません。 @No__t-0 ステートメントは、外部プロシージャへの参照を作成し、この必要な情報を提供します。

`Declare` は、モジュール レベルでのみ使用できます。 つまり、外部参照の*宣言コンテキスト*は、クラス、構造体、またはモジュールである必要があり、ソースファイル、名前空間、インターフェイス、プロシージャ、またはブロックにすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。

外部参照の既定値は[Public](../../../visual-basic/language-reference/modifiers/public.md)アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。

## <a name="rules"></a>ルール

- **アトリビュート.** 外部参照に属性を適用できます。 適用した属性は、プロジェクト内でのみ有効になり、外部ファイルには反映されません。

- **ド.** 外部プロシージャは暗黙的に[共有](../../../visual-basic/language-reference/modifiers/shared.md)されます。 外部参照を宣言するときに `Shared` キーワードを使用することはできません。また、共有状態を変更することもできません。

  外部プロシージャは、オーバーライド、インターフェイスメンバーの実装、またはイベントの処理に関与することはできません。 したがって、`Declare` ステートメントで `Overrides`、`Overridable`、`NotOverridable`、`MustOverride`、`Implements`、または `Handles` キーワードを使用することはできません。

- **外部プロシージャ名。** 外部ファイル (`aliasname`) 内のプロシージャのエントリポイント名と同じ名前 (@no__t 0) をこの外部参照に与える必要はありません。 @No__t-0 句を使用して、エントリポイント名を指定できます。 これは、外部プロシージャの名前が Visual Basic 予約済みの修飾子、変数、プロシージャ、または同じスコープ内のその他のプログラミング要素と同じである場合に便利です。

  > [!NOTE]
  > ほとんどの Dll のエントリポイント名は大文字と小文字が区別されます。

- **外部プロシージャ番号。** または、`Alias` 句を使用して、外部ファイルのエクスポートテーブル内のエントリポイントの序数を指定することもできます。 これを行うには、番号記号 (`#`) を使用して `aliasname` を開始します。 これは、Visual Basic で外部プロシージャ名に使用できない文字がある場合や、外部ファイルによってプロシージャが名前なしでエクスポートされた場合に便利です。

## <a name="data-type-rules"></a>データ型ルール

- **パラメーターのデータ型。** @No__t-0 が `On` の場合、`parameterlist` で各パラメーターのデータ型を指定する必要があります。 任意のデータ型、または列挙体、構造体、クラス、またはインターフェイスの名前を指定できます。 @No__t-0 では、`As` 句を使用して、各パラメーターに渡される引数のデータ型を指定します。

  > [!NOTE]
  > .NET Framework に対して外部プロシージャが記述されていない場合は、データ型が対応していることに注意する必要があります。 たとえば、`Integer` パラメーター (Visual Basic 6.0 で16ビット) を使用して Visual Basic 6.0 プロシージャへの外部参照を宣言する場合は、`Declare` ステートメントで、対応する引数を `Short` として指定する必要があります。これは、の16ビット整数型であるためです。Visual Basic。 同様に、@no__t 0 Visual Basic 6.0 では異なるデータ幅があり、`Date` の実装方法が異なります。

- **戻り値のデータ型。** 外部プロシージャが @no__t 0 で `Option Strict` が `On` の場合は、呼び出し元のコードに返される値のデータ型を指定する必要があります。 任意のデータ型、または列挙体、構造体、クラス、またはインターフェイスの名前を指定できます。

  > [!NOTE]
  > Visual Basic コンパイラでは、データ型が外部プロシージャのデータ型と互換性があるかどうかは検証されません。 不一致がある場合、共通言語ランタイムは、実行時に @no__t 0 例外を生成します。

- **既定のデータ型。** @No__t-0 が `Off` で、`parameterlist` のパラメーターのデータ型を指定していない場合、Visual Basic コンパイラは対応する引数を[Object データ型](../../../visual-basic/language-reference/data-types/object-data-type.md)に変換します。 同様に、`returntype` を指定しない場合、コンパイラは戻り値のデータ型を `Object` にします。

  > [!NOTE]
  > 別のプラットフォームに記述されている可能性がある外部プロシージャを扱うため、データ型についての想定を作成したり、既定値を許可したりすることは危険です。 すべてのパラメーターのデータ型と戻り値 (存在する場合) を指定する方が、はるかに安全です。 これにより、コードの読みやすさも向上します。

## <a name="behavior"></a>動作

- **検索.** 外部参照は、そのクラス、構造体、またはモジュール全体でスコープ内にあります。

- **最短.** 外部参照の有効期間は、宣言されているクラス、構造体、またはモジュールと同じです。

- **外部プロシージャを呼び出しています。** 外部プロシージャは、`Function` または `Sub` プロシージャを呼び出すのと同じ方法で呼び出すことができます。この場合、値を返す場合は式で使用し、値を返さない場合は[Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)で指定します。

  引数は、`Declare` ステートメントの `parameterlist` によって指定されたとおりに、外部プロシージャに渡すことができます。 パラメーターが外部ファイル内で最初に宣言された方法を考慮しないでください。 同様に、戻り値がある場合は、`Declare` ステートメントの `returntype` で指定されたとおりに使用します。

- **文字セット。** @No__t-0 でを指定すると、外部プロシージャを呼び出すときに Visual Basic が文字列をマーシャリングする方法を指定できます。 @No__t-0 修飾子は、すべての文字列を ANSI 値にマーシャリングするように Visual Basic に指示し、`Unicode` 修飾子は、すべての文字列を Unicode 値にマーシャリングするように指示します。 @No__t-0 修飾子は、外部参照に基づく .NET Framework 規則に従って文字列をマーシャリングするように Visual Basic に指示します。 `name`、または指定されている場合は `aliasname` です。 既定値は `Ansi` です。

  `charsetmodifier` は、Visual Basic が外部ファイル内で外部プロシージャを検索する方法も指定します。 `Ansi` および `Unicode` は、検索中に名前を変更せずに、直接 Visual Basic を参照します。 `Auto` は、次のように、ランタイムプラットフォームの基本文字セットを決定し、場合によっては外部プロシージャ名を変更するように Visual Basic に指示します。

  - Windows 95、Windows 98、または Windows Millennium Edition などの ANSI プラットフォームでは、最初に名前を変更せずに外部プロシージャを検索します。 失敗した場合は、外部プロシージャ名の末尾に "A" を追加して、もう一度確認します。

  - Windows NT、Windows 2000、Windows XP などの Unicode プラットフォームでは、最初に名前を変更せずに外部プロシージャを検索します。 失敗した場合は、外部プロシージャ名の末尾に "W" を追加して、もう一度確認します。

- **メカニズムです。** Visual Basic、.NET Framework を使用して*プラットフォーム呼び出し*(PInvoke) メカニズムを解決し、外部プロシージャにアクセスします。 `Declare`ステートメントと<xref:System.Runtime.InteropServices.DllImportAttribute>両方のクラスが自動的に、このメカニズムを使用して、PInvoke を認識する必要はありません。 詳細については、「[チュートリアル:Windows API の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)します。

> [!IMPORTANT]
> 外部プロシージャが共通言語ランタイム (CLR) の外部で実行されている場合は、*アンマネージコード*です。 このようなプロシージャ (Windows API 関数や COM メソッドなど) を呼び出すと、アプリケーションがセキュリティ上のリスクにさらされる可能性があります。 詳細については、「[アンマネージコードの安全なコーディングのガイドライン](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md)」を参照してください。

## <a name="example"></a>例

次の例では、現在のユーザー名を返す `Function` プロシージャへの外部参照を宣言しています。 次に、`getUser` プロシージャの一部として、外部プロシージャ `GetUserNameA` を呼び出します。

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>例

@No__t-0 は、アンマネージコードで関数を使用する別の方法を提供します。 次の例では、`Declare` ステートメントを使用せずにインポートされた関数を宣言します。

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)
- [チュートリアル: Windows API の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
