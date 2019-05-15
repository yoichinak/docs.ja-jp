---
title: アサーション
description: 内の式のテストのデバッグ機能として 'アサート' 式を使用する方法について説明します、F#プログラミング言語。
ms.date: 05/16/2016
ms.openlocfilehash: 5fe24195c7548e9fbb927e4b95b752c7a963c6b3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642054"
---
# <a name="assertions"></a>アサーション

`assert`式は、式のテストに使用できるデバッグ機能。 デバッグ モードでエラーが発生すると、アサーションによってシステム エラーのダイアログ ボックスが生成されます。

## <a name="syntax"></a>構文

```fsharp
assert condition
```

## <a name="remarks"></a>Remarks

`assert`式の型`bool -> unit`します。

前の構文で*条件*をテストするブール式を表します。 式が評価された場合`true`実行が影響を受けていないが続行されます。 評価されると、`false`システムのエラー ダイアログ ボックスが生成されます。 エラー ダイアログ ボックスには、文字列を含むキャプション**アサーションが失敗した**します。 ダイアログ ボックスには、アサーション エラーが発生したかを示すスタック トレースが含まれています。

デバッグ モードでコンパイルする場合にのみにアサーション チェックが有効にはつまり場合、定数`DEBUG`が定義されています。 既定で、プロジェクト システムで、`DEBUG`リリース構成ではなく、デバッグ構成で定義される定数。

使用してアサーション エラーをキャッチできないF#例外処理します。

> [!NOTE]
> `assert`関数に解決<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>します。

## <a name="example"></a>例

次のコード例の使用を示しています、`assert`式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
