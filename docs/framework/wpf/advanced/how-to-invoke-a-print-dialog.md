---
title: '方法: 印刷ダイアログ ボックスを呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 4bad8158925fea8af529f70f92aad74e2a6bbec0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254112"
---
# <a name="how-to-invoke-a-print-dialog"></a>方法: 印刷ダイアログ ボックスを呼び出す
アプリケーションから印刷できるようにするには、単にオブジェクトを<xref:System.Windows.Controls.PrintDialog>作成して開くことができます。  
  
## <a name="example"></a>例  
 コントロール<xref:System.Windows.Controls.PrintDialog>は、、構成、および XPS [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ジョブを送信するための1つのエントリポイントを提供します。 コントロールは使いやすく、マークアップまたはコードを使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]してインスタンス化できます。 次の例では、コントロールをインスタンス化してコードで開く方法と、コントロールから出力する方法を示します。 また、ダイアログで特定の範囲のページを設定するオプションをユーザーに与える方法についても説明します。 このコード例では、C: ドライブのルートに FixedDocumentSequence ファイルがあることを前提としています。  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 ダイアログが開いたら、ユーザーは自分のコンピューターにインストールされているプリンターから選択できるようになります。 また、 [MICROSOFT Xps ドキュメントライター](https://go.microsoft.com/fwlink/?LinkId=147319)を選択して、印刷ではなく XML Paper SPECIFICATION (XPS) ファイルを作成することもできます。  
  
> [!NOTE]
> このトピックで[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]説明されているの<xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType>コントロールは、Windows フォームのコンポーネントと混同しないようにする必要があります。 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>  
  
 厳密に言うと、ダイアログを<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>開くことなくメソッドを使用できます。 この意味では、コントロールは見えない印刷コンポーネントとして使用できます。 ただし、パフォーマンス上の理由から、メソッド<xref:System.Printing.PrintQueue.AddJob%2A> 、またはの多く<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>のメソッドと<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>メソッド<xref:System.Windows.Xps.XpsDocumentWriter>のいずれかを使用することをお勧めします。 詳細については、「[プログラムによる XPS ファイルの印刷](how-to-programmatically-print-xps-files.md)」と「」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.PrintDialog>
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
- [Microsoft XPS ドキュメントライター](https://go.microsoft.com/fwlink/?LinkId=147319)
