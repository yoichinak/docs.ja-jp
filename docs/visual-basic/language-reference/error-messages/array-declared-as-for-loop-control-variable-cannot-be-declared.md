---
title: ループ コントロール変数として宣言された配列を初期サイズで宣言することはできません
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: bee3bcd3701945f5cf77f6761defc8be77acf49f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843579"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>ループ コントロール変数として宣言された配列を初期サイズで宣言することはできません
A`For Each`ループとして配列を使用してその*要素*繰り返し変数は、その配列を初期化します。  
  
 次のステートメントでは、このエラーの生成方法を示しています。  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 最初の`For Each`ステートメントの要素にアクセスする正しい方法は、`arrayList`します。 2 番目の`For Each`ステートメントには、このエラーが生成されます。  
  
 **エラー ID:** BC32039  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   宣言から初期化を削除、*要素*繰り返し変数。  
  
## <a name="see-also"></a>関連項目

- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [コレクション](../../../standard/collections/index.md)
