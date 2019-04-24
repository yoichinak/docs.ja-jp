---
title: Stop ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 80d6734945324f3f517b256051486273f6b687ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827992"
---
# <a name="stop-statement-visual-basic"></a>Stop ステートメント (Visual Basic)
実行を中断します。  
  
## <a name="syntax"></a>構文  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Remarks  
 配置できる`Stop`ステートメントの実行を中断する手順で任意の場所。 使用して、`Stop`ステートメントは、コード内のブレークポイントの設定に似ています。  
  
 `Stop`ステートメントのとは異なり、実行を中断`End`、すべてのファイルを終了したり、コンパイル済み実行可能 (.exe) ファイルで検出された場合を除き、任意の変数をクリアしません。  
  
> [!NOTE]
>  場合、`Stop`統合開発環境 (IDE) の外部で実行されているコードのステートメントが検出された場合、デバッガーが呼び出されます。 これは、コードがデバッグ、または製品のモードでコンパイルするかどうかに関係なく当てはまります。  
  
## <a name="example"></a>例  
 この例では、`Stop`ステートメント内の各繰り返しの実行を中断、`For...Next`ループします。  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>関連項目

- [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
