---
title: '方法: Visual Basic で配列を並べ替える'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 680f488a98d6e7e31b3d077843514fd12f75481c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586444"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>方法: Visual Basic で配列を並べ替える
この例の配列を宣言する`String`という名前のオブジェクト`zooAnimals`、それを設定し、アルファベット順に並べ替えられます。  
  
## <a name="example"></a>例  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- アクセス、<xref:System>名前空間。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
- 配列が空 (<xref:System.ArgumentNullException>クラス)  
  
- 配列が多次元 (<xref:System.RankException>クラス)  
  
- 配列の 1 つまたは複数の要素を実装しない、<xref:System.IComparable>インターフェイス (<xref:System.InvalidOperationException>クラス)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [配列のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [コレクション](../../concepts/collections.md)
- [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
