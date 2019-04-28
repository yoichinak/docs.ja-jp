---
title: ブール演算子
description: 使用可能なブール演算子について説明します、F#プログラミング言語。
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925815"
---
# <a name="boolean-operators"></a>ブール演算子

このトピックでは、F# 言語でブール演算子のサポートについて説明します。

## <a name="summary-of-boolean-operators"></a>ブール演算子の概要

次の表では、F# 言語で使用可能なブール演算子をまとめたものです。 これらの演算子でサポートされている唯一の種類は、`bool`型。

|演算子|説明|
|--------|-----------|
|`not`|否定のブール型|
|<code>&#124;&#124;</code>|ブール型 OR|
|`&&`|ブール型 AND|

ブール型 AND および OR 演算子を実行*ショート サーキット評価*演算子の右辺の式を評価、式の全体的な結果を確認する必要がある場合にのみ、します。 2 番目の式、`&&`に最初の式が評価された場合にのみ、演算子が評価される`true`; の 2 番目の式、`||`に最初の式が評価された場合にのみ、演算子が評価される`false`します。

## <a name="see-also"></a>関連項目

- [ビット処理演算子](bitwise-operators.md)
- [算術演算子](arithmetic-operators.md)
- [シンボルと演算子のリファレンス](index.md)