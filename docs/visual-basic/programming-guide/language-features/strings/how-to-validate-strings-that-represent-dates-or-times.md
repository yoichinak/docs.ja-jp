---
title: '方法: 日付または時刻を表す文字列を検証 (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: f24ff05e48327c21c02eb92b07db17266f743a80
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815231"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>方法: 日付または時刻を表す文字列を検証 (Visual Basic)
次のコード例のセットを`Boolean`文字列が有効な日付または時刻を表すかどうかを示す値です。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 置換`("01/01/03")`と`"9:30 PM"`日付と時刻に検証したいとします。 文字列を別のハード コーディングされた文字列を置き換えることができます、`String`など、文字列を返す変数、またはメソッドで`InputBox`します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 このメソッドに変換する前に、文字列の検証を使用して、`String`を`DateTime`変数。 最初の日付または時刻をチェックする場合は、実行時に例外を生成を回避できます。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
