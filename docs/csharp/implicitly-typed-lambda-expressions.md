---
title: 暗黙的に型指定されるラムダ式
description: 暗黙的に型指定される変数宣言を使用してラムダ式を宣言することはできない理由を説明します。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: c6b0f2666a5c67ce8c89222da5959304ecb8fb93
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039133"
---
# <a name="implicitly-typed-lambda-expressions"></a>暗黙的に型指定されるラムダ式

暗黙的に型指定される変数宣言を使用してラムダ式を宣言することはできません。
そうした場合、コンパイラの循環論理問題が発生します。 `var` 宣言は、代入演算子の右辺にある式の型から変数の型を推論するようにコンパイラに指示するものです。 ラムダ式はコンパイル時の型を持ちませんが、任意の一致するデリゲートまたは式の型に変換できます。 デリゲートまたは式の型の変数にラムダ式を代入すると、"代入先の" 変数のシグネチャに一致する式またはデリゲートにラムダ式を変換するようコンパイラに指示することになります。 コンパイラは、代入の右辺の値を代入の左辺の型に一致させることを試みる必要があります。 

代入の左右どちらの側でも、代入演算子の反対側の辺のオブジェクトを調べて型が一致するかどうかを判断するようコンパイラに指示することはできません。

C# 言語でこの動作が指定されている理由については、[この記事](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf)を参照してください (PDF ダウンロード)。
