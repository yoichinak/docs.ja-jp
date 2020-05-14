---
title: If ステートメント行の外側でステートメント ブロックを終了することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 0e645ccf17d0aba702a576791622aa4e9b3dd5e0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593265"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>If ステートメント行の外側でステートメント ブロックを終了することはできません。
単一行の `If` ステートメントにコロン (:) で区切られた複数のステートメントが含まれていて、そのうちの 1 つが、単一行の `If` の外側にある制御ブロックの `End` ステートメントです。 単一行の `If` ステートメントで、`End If` ステートメントが使用されません。  
  
 **エラー ID:** BC32005  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 単一行の `If` ステートメントを、`End If` ステートメントが含まれている制御ブロックの外側に移動します。  
  
## <a name="see-also"></a>関連項目

- [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
