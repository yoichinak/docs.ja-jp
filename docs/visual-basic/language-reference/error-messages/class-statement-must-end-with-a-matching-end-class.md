---
title: "'Class' ステートメントの終わりには、対応する 'End Class' を指定しなければなりません。"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 559595e9902ec2f0a19fd6b13e2c89fa1c2b52d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602413"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a>'Class' ステートメントの終わりには、対応する 'End Class' を指定しなければなりません。
`Class` は `Class` ブロックを開始するために使用します。ブロックの先頭にのみ指定でき、対応する`End Class` ステートメントでブロックを終えます。 `Class` ステートメントが重複しているか、`Class` ブロックの最後に `End Class` が使用されませんでした。  
  
 **エラー ID:** BC30481  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 不要な `Class` ステートメントを見つけて削除します。  
  
- 一致する `End Class` で `Class` ブロックを終了します。  
  
## <a name="see-also"></a>関連項目

- [End \<キーワード> ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
