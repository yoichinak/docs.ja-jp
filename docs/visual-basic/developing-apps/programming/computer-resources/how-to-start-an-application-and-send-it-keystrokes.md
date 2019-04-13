---
title: '方法: アプリケーションを起動してキーストロークを送る (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 9519fd85177d5d2adf97b54652c19330954edadf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815967"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>方法: アプリケーションを起動してキーストロークを送る (Visual Basic)
この例では、`Shell` 関数を使用して電卓アプリケーションを起動し、`My.Computer.Keyboard.SendKeys` メソッドを使用してキーストロークを送って、2 つの数値を乗算します。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 要求されたプロセス ID のアプリケーションが見つからない場合には、<xref:System.ArgumentException> 例外が発生します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 `Shell` 関数の呼び出しには完全な信頼が必要です (<xref:System.Security.SecurityException> クラス)。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
