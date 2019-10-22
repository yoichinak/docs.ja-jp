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
ms.openlocfilehash: e9382ee34842fc3a3b4b23f71848bda602c99780
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583218"
---
# <a name="stop-statement-visual-basic"></a>Stop ステートメント (Visual Basic)
実行を中断します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Remarks  
 プロシージャ内の任意の場所に `Stop` ステートメントを配置して、実行を中断することができます。 @No__t_0 ステートメントの使用は、コードにブレークポイントを設定することと似ています。  
  
 @No__t_0 ステートメントは実行を中断しますが、`End` とは異なり、コンパイル済みの実行可能 (.exe) ファイルに存在しない限り、ファイルは閉じられず、変数はクリアされません。  
  
> [!NOTE]
> 統合開発環境 (IDE: integrated development environment) の外部で実行されているコードで `Stop` ステートメントが検出されると、デバッガーが呼び出されます。 これは、コードがデバッグモードとリテールモードのどちらでコンパイルされたかに関係なく当てはまります。  
  
## <a name="example"></a>例  
 この例では、`Stop` ステートメントを使用して、`For...Next` ループを通じて各反復処理の実行を中断します。  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>関連項目

- [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
