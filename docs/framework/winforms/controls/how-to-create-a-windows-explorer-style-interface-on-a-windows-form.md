---
title: '方法: Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: dd70feaba29e29748ac56729632fa359582a6914
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327374"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>方法: Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する
Windows エクスプ ローラーは、準備ができて、慣れ親しんだのためのアプリケーションの一般的なユーザー インターフェイス選択です。  
  
 Windows エクスプ ローラーは、基本的に、<xref:System.Windows.Forms.TreeView>コントロールと<xref:System.Windows.Forms.ListView>別のパネル上のコントロール。 パネルは、スプリッターによってサイズ変更可能で行われます。 このコントロールの配置は、情報の表示と参照は非常に効果的です。  
  
 次の手順では、Windows エクスプ ローラーのようなフォームでコントロールを配置する方法を示します。 Windows エクスプ ローラー アプリケーションのファイル参照機能を追加する方法は表示されません。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Windows エクスプ ローラー スタイルの Windows フォームを作成するには  
  
1. 新しい Windows アプリケーション プロジェクトを作成 (**ファイル** > **新規** > **プロジェクト** > **Visual c#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォーム アプリケーション**)。  
  
2. **ツールボックス**:  
  
    1.  ドラッグ、<xref:System.Windows.Forms.SplitContainer>コントロールをフォームにします。  
  
    2.  ドラッグ、<xref:System.Windows.Forms.TreeView>にコントロールを**SplitterPanel1** (のパネル、<xref:System.Windows.Forms.SplitContainer>マークされているコントロール**Panel1**)。  
  
    3.  ドラッグ、<xref:System.Windows.Forms.ListView>にコントロールを**SplitterPanel2** (のパネル、<xref:System.Windows.Forms.SplitContainer>マークされているコントロール**Panel2**)。  
  
3. CTRL キーをクリックするとさらに 3 つすべてのコントロールを選択します。 選択すると、<xref:System.Windows.Forms.SplitContainer>コントロールをパネルではなく、スプリッター バーをクリックします。  
  
    > [!NOTE]
    >  使用しないでください、**すべて選択**コマンドを**編集**メニュー。 これを行う場合、次の手順で必要なプロパティでは表示されません、**プロパティ**ウィンドウ。  
  
4. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。  
  
5. F5 キーを押してアプリケーションを実行します。  
  
     フォームには、Windows エクスプ ローラーのような 2 つの部分のユーザー インターフェイスが表示されます。  
  
    > [!NOTE]
    >  分割線をドラッグすると、パネルでは、自身サイズを変更します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.SplitContainer>
- [方法: Windows フォームでマルチペイン ユーザー インターフェイスを作成します。](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [方法: サイズ変更および位置指定動作を分割ウィンドウを定義します。](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [方法: ウィンドウを水平方向に分割します。](how-to-split-a-window-horizontally.md)
- [SplitContainer コントロール](splitcontainer-control-windows-forms.md)
