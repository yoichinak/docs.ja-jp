---
title: 配列の上下限を、型指定子に記述できません。
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f20ed883005641082eb89e2effa5221594910ffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838782"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>配列の上下限を、型指定子に記述できません。
配列のサイズは、データ型の指定子の一部として宣言することはできません。  
  
 **エラー ID:** BC30638  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   次の例に示すように、型の後に、配列のサイズを配置することではなく変数名のすぐ後の配列のサイズを指定します。  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   配列を定義し、次の例に示すように、必要な数の要素を初期化します。  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>関連項目

- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
