---
title: エラーの種類 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831567"
---
# <a name="error-types-visual-basic"></a>エラーの種類 (Visual Basic)
Visual basic でのエラー (とも呼ばれる*例外*) 3 つのカテゴリに分類されます。 構文エラー、実行時エラー、および論理エラー。  
  
## <a name="syntax-errors"></a>構文エラー  
 *構文エラー*はコードを記述するときに表示されます。 Visual Basic で入力すると、コードを確認します、**コード エディター**ウィンドウと単語のスペルが間違ってなどの言語要素を正しくを使用して、操作を誤ったアラートを通知します。 構文エラーは、エラーの最も一般的な種類です。 その解決簡単にコーディング環境で発生するとすぐにします。  
  
> [!NOTE]
>  `Option Explicit`ステートメントが構文エラーを回避する 1 つのことを意味します。 アプリケーションで使用されるすべての変数を事前に宣言を強制的にされます。 したがって、コードでこれらの変数を使用している場合、入力ミスがすぐに検出され、修正できます。  
  
## <a name="run-time-errors"></a>実行時エラー  
 *実行時エラー*は、コンパイルし、コードを実行した後にのみ出現します。 これらには、構文エラーを持ちませんが実行されませんが、正しく表示されるコードが含まれます。 たとえば、ファイルを開くためのコードの行を正しく記述可能性があります。 ファイルが壊れている場合は、アプリケーションを実行できませんが、`Open`関数、およびその実行を停止します。 ほとんどの実行時エラーを修正するには、欠陥のあるコードの書き直しを再コンパイルし、再実行することで。  
  
## <a name="logic-errors"></a>論理エラー  
 *論理エラー*は、アプリケーションが使用すると表示されます。 ユーザー アクションへの応答でほとんどの多くの場合、不要なまたは予期しない結果が表示されます。 たとえば、入力の間違いキーまたはその他の外部の影響を与える可能性が、アプリケーションに必要なパラメーター内で動作しなくなったりします。 論理エラーは、通常ではないため常に明確ではないを解決する最も困難な型です。  
  
## <a name="see-also"></a>関連項目

- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [デバッガーの基本事項](/visualstudio/debugger/debugger-basics)
