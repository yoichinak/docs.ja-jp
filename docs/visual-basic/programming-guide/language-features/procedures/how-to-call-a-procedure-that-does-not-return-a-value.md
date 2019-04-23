---
title: '方法: (Visual Basic) の値を返さないプロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 6e3ce2a184ca5411a6a016929a16bf3d67e669ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335473"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>方法: (Visual Basic) の値を返さないプロシージャを呼び出す
A`Sub`プロシージャが呼び出し元のコードに値を返しません。 明示的に呼び出す、スタンドアロンの呼び出し元ステートメントを使用します。 単に式の中で名前を使用して呼び出すことはできません。  
  
### <a name="to-call-a-sub-procedure"></a>Sub プロシージャを呼び出す  
  
1. 名前を指定、`Sub`プロシージャ。  
  
2. 引数リストを囲む中かっこでプロシージャ名に従ってください。 引数がない場合、かっこを省略することができます。 ただし、かっこを使用して、コードを読みやすくします。  
  
3. コンマで区切り、かっこ内の引数リストで、引数を配置します。 同じ順序で引数を指定するかどうかを必ずを`Sub`プロシージャが、対応するパラメーターを定義します。  
  
     次の例では、Visual Basic<xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>アプリケーション ウィンドウをアクティブ化する関数。 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> ウィンドウのタイトルを単一の引数として受け取る。 呼び出し元のコードに値を返すことはできません。 例がスローされます、メモ帳プロセスが実行されていない場合、<xref:System.ArgumentException>します。 `Shell`プロシージャでは、アプリケーションは、指定されたパスに前提としています。  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [方法: プロシージャを作成します。](./how-to-create-a-procedure.md)
- [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)
- [方法: Visual Basic でイベント ハンドラーを呼び出す](./how-to-call-an-event-handler.md)
