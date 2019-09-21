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
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957621"
---
# <a name="stop-statement-visual-basic"></a>Stop ステートメント (Visual Basic)
実行を中断します。  
  
## <a name="syntax"></a>構文  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Remarks  
 ステートメントをプロシージャ`Stop`内の任意の場所に配置して、実行を中断することができます。 `Stop`ステートメントを使用することは、コードにブレークポイントを設定することと似ています。  
  
 ステートメント`Stop`は実行を中断します`End`が、とは異なり、コンパイルされた実行可能 (.exe) ファイルに存在しない限り、ファイルを閉じたり変数をクリアしたりすることはありません。  
  
> [!NOTE]
> 統合開発環境 (IDE: integrated development environment) の外部で実行されているコードでステートメントが検出されると、デバッガーが呼び出されます。`Stop` これは、コードがデバッグモードとリテールモードのどちらでコンパイルされたかに関係なく当てはまります。  
  
## <a name="example"></a>例  
 この例では`Stop` 、ステートメントを使用し`For...Next`て、ループを通じて各反復処理の実行を中断します。  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>関連項目

- [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
