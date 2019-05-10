---
title: 配列の上下限を、型指定子に記述できません。
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 50e1cd0e41da467a9e816c8e5d64d09a36923d65
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665748"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>配列の上下限を、型指定子に記述できません。
配列のサイズは、データ型の指定子の一部として宣言することはできません。  
  
 **エラー ID:** BC30638  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 次の例に示すように、型の後に、配列のサイズを配置することではなく変数名のすぐ後の配列のサイズを指定します。  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
- 配列を定義し、次の例に示すように、必要な数の要素を初期化します。  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>関連項目

- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
