---
title: オプション
description: 名前付きの値または変数の場合、実際の値の型が存在しない F# オプションを使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 6d32693bccc74c2cab642e4f626c9463092e8a39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666483"
---
# <a name="options"></a>オプション

オプションの種類でF#名前付きの値または変数の実際の値が存在しない場合に使用されます。 オプションは、その型の値を保持できる備え、基になる型または値がいない可能性があります。

## <a name="remarks"></a>Remarks

次のコードでは、オプションの種類を生成する関数を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

ご覧のとおり場合、入力`a`は 0 より大きく、`Some(a)`が生成されます。  それ以外の場合、`None`が生成されます。

値`None`オプションには、実際の値がない場合に使用されます。 それ以外の場合、式`Some( ... )`オプションの値を提供します。 値`Some`と`None`は次の関数のように、パターン マッチングで役に立ちます`exists`、返された`true`オプションに値が設定されている場合と`false`そうでない場合。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>オプションを使用します。

オプションは一般的に使用、検索が、一致する結果を返さない場合に次のコードに示すようにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

前のコード リストは再帰的に検索します。 関数は、`tryFindMatch`は述語関数を受け取り`pred`を返すブール値、および検索するリスト。 再帰が終了し、関数が式のオプションとして値を返します、述語を満たす要素が見つかった場合`Some(head)`します。 空のリストが一致したときに、再帰は終了します。 その時点で、値`head`検出されていないと`None`が返されます。

多くの F# ライブラリ関数の戻り値がない可能性がありますまたは可能性のある値のコレクションを検索する、`option`型。 慣例により、これらの関数の開始と、`try`プレフィックス、たとえば、 [ `Seq.tryFindIndex`](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)します。

値が存在しない場合に、例では、値を構築しようとすると、例外がスローする可能性がある場合にでもオプションできますも役立ちます。 これを次のコード例に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile`前の例では関数型があります`string -> File option`返すため、`File`オブジェクト ファイルが正常に開くかどうかと`None`例外が発生した場合。 状況によっては、ある可能性がありますいないを適切な設計の選択を反映するのではなく、例外をキャッチします。

渡すことができますがさらに、`null`または値を null である、`Some`オプションの大文字と小文字です。 回避するには、通常、これは、通常のルーチンではF#はプログラミングでは、.NET での参照型の性質により、考えられる。

## <a name="option-properties-and-methods"></a>オプションのプロパティとメソッド

オプションの種類には、次のプロパティとメソッドがサポートしています。

|プロパティまたはメソッド|型|説明|
|------------------|----|-----------|
|[None](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|静的プロパティを持つオプションの値を作成することができます、`None`値。|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|返します`true`オプションの場合、`None`値。|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|返します`true`オプションがない値を持つ場合`None`します。|
|[いくつか](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|オプションを作成する静的メンバーがない値を持つ`None`します。|
|[[値]](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|基になる値を返しますまたはがスローされます、`System.NullReferenceException`値が場合`None`します。|

## <a name="option-module"></a>オプション モジュール

モジュールの場合がある[オプション](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c)オプションで操作を実行するための便利な関数を格納しています。 一部の関数は、プロパティの機能を繰り返しは、関数が必要なコンテキストで役立ちます。 [Option.isSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79)と[Option.isNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819)両方モジュール関数は、オプション値を保持するかどうかをテストします。 [Option.get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea)いずれかを使用する必要がある場合に、値を取得します。 値が存在しない場合スロー`System.ArgumentException`します。

[Option.bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0)値がある場合、関数がその値に対して関数を実行します。 関数は引数を 1 つだけを受け取る必要があり、そのパラメーターの型は、オプションの型である必要があります。 関数の戻り値は、別のオプションの種類です。

オプション モジュールには、リスト、配列、シーケンス、およびその他のコレクション型で利用可能な関数に対応する関数も含まれています。 これらの関数を含める[ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622)、 [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191)、 [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428)、 [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99)、 [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb)、 [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8)、および[ `Option.count`](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876)します。 これらの関数は、0 個または 1 つの要素のコレクションのように使用するためのオプションを有効にします。 詳細と例については、コレクション関数の説明を参照してください。[一覧](lists.md)します。

## <a name="converting-to-other-types"></a>その他の型への変換

オプションは、リストまたは配列に変換できます。 オプションは、これらのデータ構造のいずれかに変換するときに、結果として得られるデータ構造に 0 個または 1 つの要素があります。 オプションを配列に変換する[ `Option.toArray`](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64)します。 オプションをリストに変換するには使用[ `Option.toList`](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1)します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [F# の型](fsharp-types.md)
