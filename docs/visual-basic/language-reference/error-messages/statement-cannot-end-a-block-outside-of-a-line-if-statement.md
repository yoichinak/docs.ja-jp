---
title: If ステートメント行の外側でステートメント ブロックを終了することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 85573099ec0a3f8a23c17bdf384c4c105f9157df
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825795"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>If ステートメント行の外側でステートメント ブロックを終了することはできません。
単一行`If`ステートメントには、コロン (:) のうちの 1 つで区切られた複数のステートメントが含まれています、`End`単一行の外側のコントロール ブロックのステートメント`If`します。 単一行`If`ステートメントは使用しないでください、`End If`ステートメント。  
  
 **エラー ID:** BC32005  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   単一行を移動`If`ステートメントを含むコントロール ブロックの外側、`End If`ステートメント。  
  
## <a name="see-also"></a>関連項目

- [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
