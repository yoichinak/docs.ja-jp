---
title: アサーション
description: 内の式のテストのデバッグ機能として 'アサート' 式を使用する方法について説明します、F#プログラミング言語。
ms.date: 05/16/2016
ms.openlocfilehash: c2d97386e87e9b915da490a78fff9aedb9def616
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703219"
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