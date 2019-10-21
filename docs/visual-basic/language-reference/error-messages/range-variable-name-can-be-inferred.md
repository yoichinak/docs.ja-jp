---
title: 範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: ca50ddd86cfbba8db0148ed315645714acabc18d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582424"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます

1つ以上の引数を受け取るプログラミング要素は、LINQ クエリに含まれています。 コンパイラは、そのプログラミング要素から範囲変数を推論できません。

**エラー ID:** BC36599

## <a name="to-correct-this-error"></a>このエラーを解決するには

次のコードに示すように、プログラミング要素に明示的な変数名を指定します。

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
