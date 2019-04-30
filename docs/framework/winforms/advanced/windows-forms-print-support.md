---
title: Windows フォームにおける印刷のサポート
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011850"
---
# <a name="windows-forms-print-support"></a>Windows フォームにおける印刷のサポート
Windows フォームでの印刷を使用して主に構成、 [PrintDocument コンポーネント](../controls/printdocument-component-windows-forms.md)を印刷するユーザーを有効にするコンポーネントと[PrintPreviewDialog コントロール](../controls/printpreviewdialog-control-windows-forms.md)コントロール、 [PrintDialogコンポーネント](../controls/printdialog-component-windows-forms.md)と[PageSetupDialog コンポーネント](../controls/pagesetupdialog-component-windows-forms.md)Windows オペレーティング システムに慣れているユーザーに使い慣れたグラフィカル インターフェイスを提供するコンポーネント。  
  
 通常の新しいインスタンスを作成、<xref:System.Drawing.Printing.PrintDocument>コンポーネントを使用して印刷する対象を記述するプロパティを設定する、<xref:System.Drawing.Printing.PrinterSettings>と<xref:System.Drawing.Printing.PageSettings>クラス、および呼び出し、<xref:System.Drawing.Printing.PrintDocument.Print%2A>実際には、ドキュメントを印刷する方法。  
  
 Windows ベースのアプリケーションから印刷の実行中に、<xref:System.Drawing.Printing.PrintDocument>コンポーネントをユーザーに警告印刷が発生しているという事実と印刷ジョブをキャンセルできる中止の印刷 ダイアログ ボックスを表示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 標準の Windows フォーム印刷ジョブを作成します。](how-to-create-standard-windows-forms-print-jobs.md)  
 使用する方法について説明します、<xref:System.Drawing.Printing.PrintDocument>から Windows フォームを印刷するコンポーネント。  
  
 [方法: 実行時に PrintDialog のユーザー入力をキャプチャします。](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 選択した印刷オプションを使用してプログラムで変更する方法について説明します、<xref:System.Windows.Forms.PrintDialog>コンポーネント。  
  
 [方法: Windows フォームでユーザーのコンピューターに接続されているプリンターを選択します。](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 印刷を使用するプリンターの変更について説明します、<xref:System.Windows.Forms.PrintDialog>実行時にコンポーネント。  
  
 [方法: Windows フォームでグラフィックスを印刷します。](how-to-print-graphics-in-windows-forms.md)  
 プリンターに送信側のグラフィックについて説明します。  
  
 [方法: Windows フォームで複数ページのテキスト ファイルを印刷します。](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 プリンターに送信するテキストをについて説明します。  
  
 [方法: 完全な Windows フォームの印刷ジョブ](how-to-complete-windows-forms-print-jobs.md)  
 印刷ジョブの完了をユーザーに警告する方法について説明します。  
  
 [方法: Windows フォームを印刷します。](how-to-print-a-windows-form.md)  
 現在のフォームのコピーを印刷する方法を示します。  
  
 [方法: 印刷プレビューを使用して Windows フォームで印刷します。](how-to-print-in-windows-forms-using-print-preview.md)  
 使用する方法を示しています、<xref:System.Windows.Forms.PrintPreviewDialog>のドキュメントを印刷します。  
  
## <a name="related-sections"></a>関連項目  
 [PrintDocument コンポーネント](../controls/printdocument-component-windows-forms.md)  
 使用方法について説明します、<xref:System.Drawing.Printing.PrintDocument>コンポーネント。  
  
 [PrintDialog コンポーネント](../controls/printdialog-component-windows-forms.md)  
 使用方法について説明します、<xref:System.Windows.Forms.PrintDialog>コンポーネント。  
  
 [PrintPreviewDialog コントロール](../controls/printpreviewdialog-control-windows-forms.md)  
 使用方法について説明します、<xref:System.Windows.Forms.PrintPreviewDialog>コントロール。  
  
 [PageSetupDialog コンポーネント](../controls/pagesetupdialog-component-windows-forms.md)  
 使用方法について説明します、<xref:System.Windows.Forms.PageSetupDialog>コンポーネント。  
  
 <xref:System.Drawing.Printing>  
 クラスについて説明します、<xref:System.Drawing.Printing>名前空間。
