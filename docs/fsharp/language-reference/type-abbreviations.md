---
title: 型略称
description: コードを読みやすくためにわかりやすい名前の型を提供する F# 型略称について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630217"
---
# <a name="type-abbreviations"></a>型略称

*型略称*は、型の別名または代替名です。

## <a name="syntax"></a>構文

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Remarks

型の省略形を使用すると、コードを読みやすくするために、型にわかりやすい名前を付けることができます。 また、これを使用して、書き込みが煩雑な型の使いやすい名前を作成することもできます。また、型の省略形を使用すると、型を使用するすべてのコードを変更することなく、基になる型を簡単に変更できるようになります。 単純型の省略形を次に示します。

型の省略形のアクセシビリティ`public`は、既定でに設定されています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

次のコードのように、型の省略形にジェネリックパラメーターを含めることができます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

前のコードでは`Transform` 、は、任意の型の単一の引数を受け取り、同じ型の単一の値を返す関数を表す型略称です。

型の省略形は .NET Framework MSIL コードに保持されません。 したがって、F# アセンブリ .NET Framework の別の言語からを使用する場合は、型の省略形の基になる種類の名前を使用する必要があります。

型略称は、測定単位でも使用できます。 詳細については、「[測定単位](units-of-measure.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
