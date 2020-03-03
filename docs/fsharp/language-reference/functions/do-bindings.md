---
title: do バインド
description: 関数またはF#値を定義せずに ' do ' バインディングを使用してコードを実行する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630530"
---
# <a name="do-bindings"></a>do バインド

バインディング`do`は、関数または値を定義せずにコードを実行するために使用されます。 また、バインディングはクラスで使用できます。「 [ `do`クラスのバインディング](../members/do-bindings-in-classes.md)」を参照してください。

## <a name="syntax"></a>構文

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Remarks

関数また`do`は値の定義とは別にコードを実行する場合は、バインディングを使用します。 `do`バインディング内の式はを返す`unit`必要があります。 最上位レベル`do`のバインド内のコードは、モジュールが初期化されるときに実行されます。 キーワード`do`は省略可能です。

最上位レベル`do`のバインドに属性を適用できます。 たとえば、プログラムが COM 相互運用機能を使用している場合は、 `STAThread`プログラムに属性を適用できます。 これを行うには、次のコードに`do`示すように、バインディングの属性を使用します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](../index.md)
- [関数](index.md)
