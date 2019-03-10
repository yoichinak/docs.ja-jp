---
title: '方法: Windows フォームを印刷します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: 80bf88ad048e55a381d034d2a796de6f77f8691c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714152"
---
# <a name="how-to-print-a-windows-form"></a>方法: Windows フォームを印刷します。
開発プロセスの一環として、通常は印刷する、Windows フォームのコピー。 次のコード例を使用して、現在のフォームのコピーを印刷する方法を示しています、<xref:System.Drawing.Graphics.CopyFromScreen%2A>メソッド。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 これは、完全なコード例を含む、`Main`メソッド。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   プリンターにアクセスするためのアクセス許可がありません。  
  
-   プリンターをインストールすることはありません。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 このコード例を実行するのには、コンピューターで使用するプリンターにアクセスするためのアクセス許可が必要です。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Printing.PrintDocument>
- [方法: GDI + を使用したイメージをレンダリングします。](how-to-render-images-with-gdi.md)
- [方法: Windows フォームでグラフィックスを印刷します。](how-to-print-graphics-in-windows-forms.md)
