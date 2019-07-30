---
title: アサーション
description: F#プログラミング言語で式をテストするためのデバッグ機能として ' assert ' 式を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630027"
---
# <a name="assertions"></a>アサーション

`assert`式は、式をテストするために使用できるデバッグ機能です。 デバッグ モードでエラーが発生すると、アサーションによってシステム エラーのダイアログ ボックスが生成されます。

## <a name="syntax"></a>構文

```fsharp
assert condition
```

## <a name="remarks"></a>Remarks

式`assert`の型`bool -> unit`がです。

前の構文では、 *condition*はテスト対象のブール式を表します。 式がに`true`評価された場合、実行は影響を受けません。 と評価`false`されると、システムエラーダイアログボックスが生成されます。 エラーダイアログボックスには、文字列の**アサーションに失敗**したキャプションが含まれています。 ダイアログボックスには、アサーションエラーが発生した場所を示すスタックトレースが含まれています。

アサーションチェックは、デバッグモードでコンパイルした場合にのみ有効になります。つまり、定数`DEBUG`が定義されている場合はです。 既定では、プロジェクトシステムでは、 `DEBUG`定数はデバッグ構成で定義されていますが、リリース構成では定義されていません。

例外処理を使用しF#てアサーションエラーをキャッチすることはできません。

> [!NOTE]
> 関数`assert`は、に<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>解決されます。

## <a name="example"></a>例

次のコード例は、 `assert`式の使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
