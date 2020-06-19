---
title: Stop ステートメント
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
ms.openlocfilehash: 497c5f207b2228412411cc3eb01976564f82bd6c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346466"
---
# <a name="stop-statement-visual-basic"></a>Stop ステートメント (Visual Basic)
実行を中断します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Remarks  
 プロシージャ内のどこでも `Stop` ステートメントを配置して、実行を中断できます。 `Stop` ステートメントの使用は、コードにブレークポイントを設定することと似ています。  
  
 `Stop` ステートメントでは実行が中断されますが、`End` とは異なり、コンパイル済みの実行可能 (.exe) ファイルで検出されていない限り、ファイルを閉じたり、変数をクリアしたりしません。  
  
> [!NOTE]
> 統合開発環境 (IDE) の外部で実行されているコードで `Stop` ステートメントが検出されると、デバッガーが呼び出されます。 これは、コードがデバッグ モードと製品版モードのどちらでコンパイルされたかに関係なく当てはまります。  
  
## <a name="example"></a>例  
 この例では、`Stop` ステートメントを使用して、`For...Next` ループを通した反復ごとに実行を中断しています。  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>関連項目

- [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
