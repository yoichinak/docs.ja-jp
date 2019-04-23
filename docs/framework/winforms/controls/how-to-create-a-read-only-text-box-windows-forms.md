---
title: '方法: 読み取り専用テキスト ボックス (Windows フォーム) を作成します。'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 72dc188993474ad4b39f0cfa74cadffdb99ff46f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308576"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>方法: 読み取り専用テキスト ボックス (Windows フォーム) を作成します。
編集可能な Windows フォームのテキスト ボックスは読み取り専用のコントロールに変換できます。 たとえば、テキスト ボックスが通常は編集ができない可能性があります現時点では、アプリケーションの状態が原因値を表示する可能性があります。  
  
### <a name="to-create-a-read-only-text-box"></a>読み取り専用テキスト ボックスを作成するには  
  
1. 設定、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>プロパティを`true`します。 プロパティを設定して`true`ユーザーがまだスクロールやテキスト ボックス内のテキストを強調表示、変更を許可しません。 A**コピー**コマンドは、テキスト ボックスでは、機能ですが**切り取り**と**貼り付け**のコマンドはできません。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>プロパティでは、実行時にユーザーとの対話のみに影響します。 まだ変更テキスト ボックスの内容プログラムで実行時に変更することで、<xref:System.Windows.Forms.TextBox.Text%2A>テキスト ボックスのプロパティ。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextBox>
- [TextBox コントロールの概要](textbox-control-overview-windows-forms.md)
- [方法: Windows フォーム TextBox コントロールでのカーソル位置を制御します。](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [方法: Windows フォーム TextBox コントロールでパスワード テキスト ボックスを作成します。](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [方法: 文字列に引用符を挿入します。](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [方法: Windows フォームの TextBox コントロールでテキストを選択します。](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [方法: Windows フォームの TextBox コントロールで複数の行を表示します。](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox コントロール](textbox-control-windows-forms.md)
