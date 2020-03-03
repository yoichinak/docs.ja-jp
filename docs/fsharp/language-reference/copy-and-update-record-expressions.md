---
title: レコード式のコピーと更新
description: 既存のレコードまたは匿名レコードをコピーし、指定したフィールドを更新して、更新されたレコードまたは匿名レコードを返す "コピーおよび更新式" を作成する方法について説明します。
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630378"
---
# <a name="copy-and-update-record-expressions"></a>レコード式のコピーと更新

*レコード式のコピーと更新*は、既存のレコードをコピーし、指定されたフィールドを更新して、更新されたレコードを返す式です。

## <a name="syntax"></a>構文

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Remarks

既定では、レコードおよび匿名レコードは不変であり、可能な限り既存のレコードに対する更新は行われません。 更新されたレコードを作成するには、レコードのすべてのフィールドを再度指定する必要があります。 このタスクを簡略化するために、*コピーと更新の式*を使用できます。 この式は、既存のレコードを取得し、式から指定されたフィールドと、式で指定されていないフィールドを使用して、同じ型の新しいものを作成します。

これは、既存のレコードをコピーする必要があり、フィールド値の一部を変更する必要がある場合に便利です。

新しく作成されたレコードのインスタンスを取得します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

そのレコードのフィールドのみを更新する場合は、次のような*コピーと更新のレコード式*を使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>関連項目

- [レコード](records.md)
- [匿名レコード](anonymous-records.md)
- [F# 言語リファレンス](index.md)
