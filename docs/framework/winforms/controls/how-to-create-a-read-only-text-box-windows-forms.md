---
title: '方法: 読み取り専用のテキストボックスを作成する (Windows フォーム)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 18d2f5ed2530957487ac25c3eb6240f8bc50a938
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971943"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>方法: 読み取り専用のテキストボックスを作成する (Windows フォーム)

編集可能な Windows フォームテキストボックスを読み取り専用のコントロールに変換できます。 たとえば、テキストボックスには通常は編集されているが、現在はアプリケーションの状態によっては編集されていない値が表示される場合があります。

## <a name="to-create-a-read-only-text-box"></a>読み取り専用のテキストボックスを作成するには

1. コントロールの<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>プロパティをに`true`設定します。 <xref:System.Windows.Forms.TextBox> プロパティがに`true`設定されている場合でも、ユーザーはテキストボックス内のテキストをスクロールして強調表示することができ、変更は許可されません。 **Copy**コマンドはテキストボックスで機能しますが、**切り取り**と**貼り付け**のコマンドは機能しません。

    > [!NOTE]
    > プロパティ<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>は、実行時のユーザーの操作にのみ影響します。 テキストボックスの内容は、テキストボックスのプロパティを変更すること<xref:System.Windows.Forms.TextBox.Text%2A>で、実行時にプログラムによって変更することもできます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextBox>
- [TextBox コントロールの概要](textbox-control-overview-windows-forms.md)
- [方法: Windows フォーム TextBox コントロールでのカーソル位置の制御](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [方法: Windows フォーム TextBox コントロールを使用してパスワードテキストボックスを作成する](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [方法: 文字列内に引用符を挿入する](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [方法: Windows フォーム TextBox コントロールでのテキストの選択](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [方法: Windows フォーム TextBox コントロールで複数の行を表示する](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox コントロール](textbox-control-windows-forms.md)
