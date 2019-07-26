---
title: 配列の上下限を、型指定子に記述できません。
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 951f710160ae1023671773c21c73946f5ae94c2b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512764"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>配列の上下限を、型指定子に記述できません。

配列のサイズをデータ型指定子の一部として宣言することはできません。

**エラー ID:** BC30638

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 次の例に示すように、配列のサイズを型の後に配置するのではなく、変数名のすぐ後に配列のサイズを指定します。

  ```vb
  Dim Array(8) As Integer
  ```

- 次の例に示すように、配列を定義し、必要な数の要素を使用して初期化します。

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a>関連項目

- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
