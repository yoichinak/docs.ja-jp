---
title: インデックス番号がインデックス付き配列の次元を超えています。
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 76cf0a997e9ad36ab4b5dfdc7c4bc29c57d309eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665693"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>インデックス番号がインデックス付き配列の次元を超えています。
配列要素にアクセスするために使用されるインデックスの数は、配列のランク、つまり配列に宣言した次元の数とまったく同じである必要があります。  
  
 **エラー ID:** BC30106  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 添字の合計数には、配列のランクと同じになるまでは、配列参照からの添字を削除します。 例えば:  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a>関連項目

- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
