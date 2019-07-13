---
title: "'ReDim' で次元数を変更することはできません"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 1e9695bbc7f104aa741de232f1f6d3c76df2cebf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591742"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>'ReDim' で次元数を変更することはできません
`ReDim` ステートメントを使用して、配列のランク (次元の数) を変更する操作が行われました。 `ReDim` は既に宣言された配列の 1 つ以上の次元のサイズを変更するために使用できますが、配列のランクを変更することはできません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 次元のサイズではなく、配列のランクを変更しようとしていることを確認します。可能な場合は、 `Dim` を使用して、希望のランクを持つ配列を新規に宣言します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における配列](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Visual Basic で配列の次元](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim ステートメント](../../visual-basic/language-reference/statements/redim-statement.md)
- [Dim ステートメント](../../visual-basic/language-reference/statements/dim-statement.md)
