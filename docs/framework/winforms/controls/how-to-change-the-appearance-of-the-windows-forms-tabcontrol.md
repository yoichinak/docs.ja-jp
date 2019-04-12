---
title: '方法: Windows フォーム TabControl の表示形式を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 05df05a52914f27a4b62cf7bde92e5d942b6ea06
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331339"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>方法: Windows フォーム TabControl の表示形式を変更する
プロパティを使用して Windows フォームのタブの外観を変更することができます、<xref:System.Windows.Forms.TabControl>と<xref:System.Windows.Forms.TabPage>コントロールの個々 のタブを構成するオブジェクト。 これらのプロパティを設定することができますタブ上のイメージを表示、水平方向にではなく縦方向にタブが表示されます、タブなどの複数の行を表示し有効または無効にタブ プログラムでします。  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>タブのラベルのアイコンを表示するには  
  
1. 追加、<xref:System.Windows.Forms.ImageList>コントロールをフォームにします。  
  
2. イメージをイメージ リストに追加します。  
  
     イメージ リストの詳細については、次を参照してください。 [ImageList コンポーネント](imagelist-component-windows-forms.md)と[方法。追加または削除のイメージで、Windows フォームの ImageList コンポーネント](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)します。  
  
3. 設定、<xref:System.Windows.Forms.TabControl.ImageList%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>を<xref:System.Windows.Forms.ImageList>コントロール。  
  
4. 設定、<xref:System.Windows.Forms.TabPage.ImageIndex%2A>のプロパティ、<xref:System.Windows.Forms.TabPage>リスト内の適切なイメージのインデックスにします。  
  
### <a name="to-create-multiple-rows-of-tabs"></a>複数行のタブを作成するには  
  
1. 選択するタブ ページの数を追加します。  
  
2. 設定、<xref:System.Windows.Forms.TabControl.Multiline%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>に`true`します。  
  
3. 複数の行にタブは表示されていない場合は、設定、<xref:System.Windows.Forms.Control.Width%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>より、すべてのタブ幅を狭くします。  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>コントロールの横にあるタブを配置するには  
  
-   設定、<xref:System.Windows.Forms.TabControl.Alignment%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>に<xref:System.Windows.Forms.TabAlignment.Left>または<xref:System.Windows.Forms.TabAlignment.Right>します。  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>プログラムで有効にまたはタブのすべてのコントロールを無効にするには  
  
1. 設定、<xref:System.Windows.Forms.TabPage.Enabled%2A>のプロパティ、<xref:System.Windows.Forms.TabPage>に`true`または`false`します。  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>タブのボタンとして表示するには  
  
-   設定、<xref:System.Windows.Forms.TabControl.Appearance%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>に<xref:System.Windows.Forms.TabAppearance.Buttons>または<xref:System.Windows.Forms.TabAppearance.FlatButtons>します。  
  
## <a name="see-also"></a>関連項目

- [TabControl コントロール](tabcontrol-control-windows-forms.md)
- [TabControl コントロールの概要 (Windows フォーム)](tabcontrol-control-overview-windows-forms.md)
- [方法: タブ ページにコントロールを追加する](how-to-add-a-control-to-a-tab-page.md)
- [方法: タブ ページを無効化する](how-to-disable-tab-pages.md)
- [方法: Windows フォーム TabControl のタブを追加および削除する](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
