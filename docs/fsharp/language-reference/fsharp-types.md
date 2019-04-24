---
title: F# の型
description: 使用される種類について学ぶF#とどのようにF#型の名前し、説明。
ms.date: 05/16/2016
ms.openlocfilehash: b48376c80b48df210bf7bc699a769d40fec60864
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193591"
---
# <a name="f-types"></a>F# の型

このトピックで説明で使用される型F#とどのようにF#型の名前し、説明。

## <a name="summary-of-f-types"></a>概要F#型
いくつかの型は考慮*プリミティブ型*、ブール型など`bool`と型バイトと文字を含む、さまざまなサイズの整数と浮動小数点型。 これらの型が記載されて[プリミティブ型](primitive-types.md)します。

言語に組み込まれている他の種類は、タプル、リスト、配列、シーケンス、レコードを含めるし、判別共用体。 学習を他の .NET 言語の経験があるにF#、これらの型の各トピックを参照する必要があります。 これらの種類についての詳細情報へのリンクが記載されて、[関連トピック](https://msdn.microsoft.com/library/#rel)このトピックの「します。 これらF#-特定の種類は、関数型プログラミング言語に共通するスタイルのプログラミングをサポートします。 これらの型の多くのモジュールが関連付けられている、F#これらの種類の一般的な操作をサポートするライブラリ。

関数の型は、パラメーターの型に関する情報が含まれていて、型を返します。

.NET Framework は、オブジェクトの種類、インターフェイス型、デリゲート型、およびその他のユーザーのソースです。 他の .NET 言語と同様、独自のオブジェクト型を定義できます。

また、F#コードは、という名前のエイリアスを定義できます*省略名を入力*、型の代替名であります。 型は、後で変わる可能性があり、種類に依存するコードを変更しないようにする型の省略形を使用する可能性があります。 または、構成コードが読み、理解しやすくするタイプのフレンドリ名として型の省略形を使用する場合があります。

F#関数型プログラミングの注意のように設計された便利なコレクション型を提供します。 これらのコレクション型を使用すると、スタイルでより高機能なコードを記述できます。 詳細については、次を参照してください。 [ F#コレクション型](fsharp-collection-types.md)します。

## <a name="syntax-for-types"></a>型の構文
F#コードでは、多くの場合、記述する必要が out 型の名前。 すべての型が構文の形式と型の注釈、抽象メソッドの宣言、デリゲートの宣言、署名、およびその他のコンストラクトでこれらの構文形式を使用します。 インタープリターで、新しいプログラム コンス トラクターを宣言するたびにその型の構造と構文の名前が出力されます。 この構文は、単なるユーザー定義型の識別子または組み込み識別子としてのような可能性があります`int`または`string`がより複雑な型の場合、構文は複雑です。

次の表に、型の構文の側面F#型。

|型|型の構文|使用例|
|----|-----------|--------|
|プリミティブ型|*type-name*|`int`<br /><br />`float`<br /><br />`string`|
|集計の種類 (クラス、構造体、共用体、レコード、列挙型、およびなど)|*type-name*|`System.DateTime`<br /><br />`Color`|
|型略称|*type-abbreviation-name*|`bigint`|
|完全修飾型|*namespaces.type-name*<br /><br />または<br /><br />*modules.type-name*<br /><br />または<br /><br />*namespaces.modules.type-name*|`System.IO.StreamWriter`|
|array|*型名*または<br /><br />*型名*配列|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|2 次元配列|*type-name*[,]|`int[,]`<br /><br />`float[,]`|
|3 次元の配列|*type-name*[,,]|`float[,,]`|
|tuple|*型 name1* &#42; *型 name2* .|たとえば、`(1,'b',3)`型があります `int * char * int`|
|ジェネリック型|*type-parameter* *generic-type-name*<br /><br />または<br /><br />*generic-type-name*&lt;*type-parameter-list*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|構築された型 (指定された特定の型引数を持つジェネリック型)|*型引数* *ジェネリック型名*<br /><br />または<br /><br />*generic-type-name*&lt;*type-argument-list*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|1 つのパラメーターを含む関数の種類|*parameter-type1* -&gt; *return-type*|受け取る関数、`int`を返します、`string`型があります `int -> string`|
|複数のパラメーターを含む関数の種類|*parameter-type1* -&gt; *parameter-type2* -&gt; ... -&gt; *return-type*|受け取る関数、`int`と`float`を返します、`string`型があります `int -> float -> string`|
|パラメーターとして高階関数|(*関数型*)|`List.map` 型があります。 `('a -> 'b) -> 'a list -> 'b list`|
|delegate|デリゲートの*関数型*|`delegate of unit -> int`|
|フレキシブル型|#*type-name*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>関連トピック

|トピック|説明|
|-----|-----------|
|[プリミティブ型](primitive-types.md)|整数型、ブール型の文字型などの組み込み単純型について説明します。|
|[Unit 型](unit-type.md)|について説明します、`unit`と等価です型、型を持つ 1 つの値と () で示されるを`void`でC#と`Nothing`Visual Basic でします。|
|[タプル](tuples.md)|タプル型、関連付けられている値のペア、3 要素、4 倍でグループ化された任意の型で構成される型について説明します。|
|[オプション](options.md)|オプション型である可能性がありますか、値または空にする型について説明します。|
|[リスト](lists.md)|リストは順序付けられた、変更できない一連の要素について説明します、同じ種類のすべて。|
|[配列](arrays.md)|配列で、一連の連続するメモリ ブロックを占有し、固定サイズの同じ種類の変更可能な要素は順序付けについて説明します。|
|[シーケンス](sequences.md)|表す論理的な一連の値のシーケンスの種類について説明します個々 の値は、必要な場合だけに計算されます。|
|[レコード](records.md)|レコードの種類、名前付きの値の小さい集計について説明します。|
|[判別共用体](discriminated-unions.md)|判別共用体型、値を持つ、一連の可能な型のいずれかの型について説明します。|
|[関数](functions/index.md)|関数の値について説明します。|
|[クラス](classes.md)|クラス型を .NET 参照型に対応するオブジェクトの種類について説明します。 クラス型は、メンバー、プロパティ、実装されるインターフェイスおよび基本データ型に含めることができます。|
|[構造体](structures.md)|について説明します、 `struct` .NET 値型に対応するオブジェクト型の型。 `struct`型は、通常、データの小規模の集計を表します。|
|[インターフェイス](interfaces.md)|特定の機能を提供する、データはありませんが、メンバーのセットを表す型がインターフェイスの型について説明します。 使用するオブジェクトの種類では、インターフェイス型を実装する必要があります。|
|[デリゲート](delegates.md)|オブジェクトとして関数を表すデリゲートの型について説明します。|
|[列挙型](enumerations.md)|列挙型、値を持つが名前付きの値のセットに属するについて説明します。|
|[属性](attributes.md)|別の型のメタデータを指定するための属性について説明します。|
|[例外の種類](exception-handling/exception-types.md)|エラー情報を指定の例外について説明します。|
