---
title: オプション
description: 名前付きの値または変数の場合、実際の値の型が存在しない F# オプションを使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 9326cf04f53adac7422c09a49a59c4eecd49486d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627350"
---
# <a name="options"></a>オプション

のF#オプションの種類は、名前付きの値または変数に実際の値が存在しない可能性がある場合に使用されます。 オプションには基になる型があり、その型の値を保持できるか、値がない可能性があります。

## <a name="remarks"></a>Remarks

次のコードは、オプションの型を生成する関数を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

ご覧のように、入力`a`が`Some(a)` 0 より大きい場合はが生成されます。  それ以外`None`の場合は、が生成されます。

値`None`は、オプションに実際の値がない場合に使用されます。 それ以外の場合`Some( ... )` 、この式はオプションに値を与えます。 値`Some` `true`と`None`は、次の関数のように、パターンマッチングに`exists`役立ちます。この関数は、オプションに値`false`がある場合はを返し、そうでない場合はを返します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>オプションの使用

オプションは、次のコードに示すように、検索で一致する結果が返されない場合によく使用されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

前のコードでは、リストは再帰的に検索されます。 関数`tryFindMatch`は、ブール値と`pred`検索するリストを返す述語関数を受け取ります。 述語を満たす要素が見つかった場合、再帰は終了し、関数は式`Some(head)`のオプションとして値を返します。 空のリストが一致すると、再帰は終了します。 その時点では、 `head`値が見つから`None`なかったため、が返されます。

多くの F# ライブラリ関数の戻り値がない可能性がありますまたは可能性のある値のコレクションを検索する、`option`型。 慣例により、これらの関数は`try` 、などの[`Seq.tryFindIndex`](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)プレフィックスで始まります。

オプションは、値が存在しない場合にも役立ちます。たとえば、値を構築しようとしたときに例外がスローされる可能性がある場合などです。 これを次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

前`openFile`の例の関数は、ファイル`string -> File option`が正常に`None`開か`File`れた場合にオブジェクトを返し、例外が発生した場合にはオブジェクトを返すため、型があります。 状況によっては、伝達を許可するのではなく、例外をキャッチするための適切な設計選択ではない場合があります。

また、オプションの`null` `Some`場合は、または null の値を渡すこともできます。 通常、これは避けてください。通常はルーチンF#プログラミングですが、.net の参照型の性質によって可能です。

## <a name="option-properties-and-methods"></a>オプションのプロパティとメソッド

オプションの種類は、次のプロパティとメソッドをサポートしています。

|プロパティまたはメソッド|種類|説明|
|------------------|----|-----------|
|[None](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|`None`値を持つオプション値を作成できるようにする静的プロパティ。|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|オプション`true`に`None`値がある場合は、を返します。|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|オプション`true`に以外`None`の値がある場合は、を返します。|
|[一部](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|値がではない`None`オプションを作成する静的メンバー。|
|[[値]](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|基になる値を返すか、 `System.NullReferenceException`値が`None`の場合はをスローします。|

## <a name="option-module"></a>オプションモジュール

[オプション](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c) に対して操作を実行する便利な関数を含むモジュールがあります。 一部の関数はプロパティの機能を繰り返しますが、関数が必要なコンテキストで役に立ちます。 [IsNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819)は、オプションが値を保持しているかどうかをテストするモジュール関数でもあり[ます](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79)。 [オプション。 get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea)は値を取得します (存在する場合)。 値がない場合は、をスロー `System.ArgumentException`します。

値がある場合、 [bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0)関数は値に対して関数を実行します。 関数は、引数を1つだけ受け取る必要があります。また、パラメーターの型は、オプションの型である必要があります。 関数の戻り値は、もう1つのオプションの種類です。

オプションモジュールには、リスト、配列、シーケンス、およびその他のコレクション型で使用できる関数に対応する関数も含まれています。 これらの関数[`Option.map`](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622) [`Option.iter`](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191) [`Option.exists`](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99) [`Option.foldBack`](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb)[には`Option.fold`](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8)、、、 [、、`Option.count`](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876)、、およびがあります。 [`Option.forall`](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428) これらの関数は、0個または1個の要素のコレクションのようにオプションを使用できます。 詳細と例については、コレクション関数の[一覧](lists.md)での説明を参照してください。

## <a name="converting-to-other-types"></a>他の型への変換

オプションは、リストまたは配列に変換できます。 オプションがこれらのデータ構造体のいずれかに変換されると、結果のデータ構造体には0個または1個の要素が含まれます。 オプションを配列に変換するには、 [`Option.toArray`](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64)を使用します。 オプションを一覧に変換するには、 [`Option.toList`](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1)を使用します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [F# の型](fsharp-types.md)
