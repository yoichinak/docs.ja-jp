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
ms.openlocfilehash: 038e259810111d2d648c72a9f43afabe11a07f29
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358432"
---
# <a name="how-to-invoke-a-print-dialog"></a>方法: 印刷ダイアログ ボックスを呼び出す
アプリケーションから印刷する機能を提供することが単に作成して開くと、<xref:System.Windows.Controls.PrintDialog>オブジェクト。  
  
## <a name="example"></a>例  
 
  <xref:System.Windows.Controls.PrintDialog> コントロールには、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、構成、および [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ジョブの送信用の 1 つのエントリ ポイントが用意されています。 コントロールは使いやすいを使用してインスタンス化することができます[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]マークアップまたはコード。 次の例では、インスタンス化し、コードで、コントロールを開く方法およびそのプリンターから印刷する方法を示します。 ダイアログは、ユーザーを特定のページ範囲を設定するオプションを確認する方法も示します。 コード例では、FixedDocumentSequence.xps c: ドライブのルート内のファイルがあることを前提としています。  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 ダイアログ ボックスが開いたら、ユーザーはコンピューターにインストールされているプリンターからを選択することになります。 選択した場合のオプションもありますが、 [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)を作成する、[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]印刷ではなくファイル。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>のコントロール[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、このトピックでこれについては説明する必要がありますと混同しないで、 <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> Windows フォームのコンポーネント。  
  
 使用する厳密に言えば、<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>ダイアログを開くことがなくメソッド。 その意味で、コントロールを非表示の印刷コンポーネントとして使用できます。 パフォーマンス上の理由から、いずれかを使用する方がよい場合がなりますが、<xref:System.Printing.PrintQueue.AddJob%2A>メソッドまたはその、多数の<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>と<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>のメソッド、<xref:System.Windows.Xps.XpsDocumentWriter>します。 詳細については、これは、次を参照してください。 [XPS ファイルをプログラムによって印刷](how-to-programmatically-print-xps-files.md)とします。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.PrintDialog>
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
- [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)
