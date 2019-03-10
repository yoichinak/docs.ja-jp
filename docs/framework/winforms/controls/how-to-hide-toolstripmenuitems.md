---
title: '方法: ToolStripMenuItems を非表示にします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: a82df42240ae045f0d6f355f642acfb8082c87a5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715257"
---
# <a name="how-to-hide-toolstripmenuitems"></a>方法: ToolStripMenuItems を非表示にします。
メニュー項目を非表示には、アプリケーションのユーザー インターフェイスを制御し、ユーザーのコマンドを制限する方法です。 多くの場合、すべてのメニュー項目が利用できない場合は、メニュー全体を非表示にするされます。 これは、ユーザーの混乱を表示します。 さらに、非表示だけでは、ユーザーはショートカット キーを使用してメニュー コマンドへのアクセスを非表示にして、メニューまたはメニュー項目を無効にする可能性があります。  
  
### <a name="to-hide-any-menu-item-programmatically"></a>任意のメニュー項目をプログラムで非表示にするには  
  
-   メニュー項目のプロパティを設定するメソッド内で設定するコードを追加、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>プロパティを`false`します。  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
- [方法: ToolStripMenuItems を無効にします。](how-to-disable-toolstripmenuitems.md)
