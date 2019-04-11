---
title: '方法: Windows フォームで複数ページのテキスト ファイルを印刷する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: b17ddcb22f3e1b7dc181e977a0227db5490b66fa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330208"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>方法: Windows フォームで複数ページのテキスト ファイルを印刷する
Windows ベースのアプリケーションでは、テキストを印刷することは非常に一般的です。 <xref:System.Drawing.Graphics> クラスは、画面やプリンターなどのデバイスにオブジェクト (グラフィックスやテキスト) を描画するためのメソッドを提供します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer> の <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドでは、印刷はサポートされていません。 印刷用にテキストを描画するには、次のコード例で示すように、<xref:System.Drawing.Graphics> の <xref:System.Drawing.Graphics.DrawString%2A> メソッドを常に使用する必要があります。  
  
### <a name="to-print-text"></a>テキストを印刷するには  
  
1. フォームに <xref:System.Drawing.Printing.PrintDocument> コンポーネントと文字列を追加します。  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. ドキュメントを印刷する場合は、<xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> プロパティを印刷するドキュメントに設定し、ドキュメントの内容を開いて前に追加した文字列に読み取ります。  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベント ハンドラーで、<xref:System.Drawing.Printing.PrintPageEventArgs> クラスの <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> プロパティとドキュメントの内容を使用して、行の長さと 1 ページあたりの行数を計算します。 各ページを描画した後で、最後のページかどうかを確認し、<xref:System.Drawing.Printing.PrintPageEventArgs> の <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> プロパティを適切に設定します。 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> が `false` になるまで <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントが発生します。 また、<xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントがイベント処理メソッドに関連付けられていることを確認します。  
  
     次のコード例では、イベント ハンドラーは、フォームで使用されているものと同じフォントで "testPage.txt" ファイルの内容を印刷するために使用されます。  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <xref:System.Drawing.Printing.PrintDocument.Print%2A> メソッドを呼び出して <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントを発生させます。  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>例  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   C:\\ ドライブのルートにある、印刷するテキストを含む testPage.txt という名前のテキスト ファイル。 別のファイルを印刷するようコードを編集します。  
  
-   System、System.Windows.Forms、System.Drawing の各アセンブリへの参照。  
  
-   コマンドラインからこの例を Visual Basic または Visual C# の構築方法の詳細については、[コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Windows フォームにおける印刷のサポート](windows-forms-print-support.md)
