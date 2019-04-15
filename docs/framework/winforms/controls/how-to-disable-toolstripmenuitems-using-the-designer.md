---
title: '方法: デザイナーを使用して ToolStripMenuItems を無効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 9965825458afcd50b29699c3b89ed506078e04d9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338060"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>方法: デザイナーを使用して ToolStripMenuItems を無効にする
制限またはユーザーが実行を有効にして、ユーザーのアクティビティへの応答でのメニュー項目を無効にすると、コマンドの範囲を広げることができます。 これらが作成されますが、これで調整時にメニュー項目が既定で有効に、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティ。 デザイン時にこのプロパティを操作することができます、**プロパティ**ウィンドウまたはプログラムによってコードで設定します。 詳細については、「[方法 :ToolStripMenuItems を無効にする](how-to-disable-toolstripmenuitems.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>デザイン時にメニュー項目を無効にするには  
  
1. フォームで選択されたメニュー項目を設定、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティを`false`します。  
  
    > [!TIP]
    >  メニューの最初または最上位のメニュー項目を無効にするには、メニュー内に含まれるすべてのメニュー項目が無効にします。 同様に、サブメニュー項目を持つメニュー項目を無効にするには、項目のサブメニュー項目が無効にします。 指定されたメニューのすべてのコマンドがユーザーに使用可能な場合は、これは、ユーザー インターフェイスを簡潔に非表示にして、メニュー全体を無効にすることをお勧めプログラミングと見なされます。 非表示にする必要があり、単独で非表示がショートカット キーを使用してメニュー コマンドにアクセスを妨げないもの、メニューを無効にします。 設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>トップレベルのメニュー項目のプロパティ`false`メニュー全体を非表示にします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [方法: ToolStripMenuItems を非表示にする](how-to-hide-toolstripmenuitems.md)
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
