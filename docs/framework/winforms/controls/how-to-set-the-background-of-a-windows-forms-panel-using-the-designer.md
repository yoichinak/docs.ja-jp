---
title: '方法: デザイナーを使って Windows フォーム パネルの背景を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 888b1910902819b847d7d622f7b086fec82d669d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334355"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>方法: デザイナーを使って Windows フォーム パネルの背景を設定する
Windows フォーム<xref:System.Windows.Forms.Panel>コントロールは、背景色と背景イメージの両方を表示できます。 <xref:System.Windows.Forms.Control.BackColor%2A>プロパティ パネルで、ラベルなどが含まれており、ラジオ ボタン コントロールの背景色を設定します。 場合、<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティが設定されていない、<xref:System.Windows.Forms.Control.BackColor%2A>選択がパネルのすべてを入力します。 場合、<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティが設定されて、パネルに含まれるコントロールの背後にある画像が表示されます。  
  
 次の手順が必要です、 **Windows アプリケーション**を含むフォームを使用してプロジェクトを<xref:System.Windows.Forms.Panel>コントロール。 このようなプロジェクトを設定する方法については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Windows フォーム デザイナーの背景を設定するには  
  
1. <xref:System.Windows.Forms.Panel> コントロールを選択します。  
  
2. **プロパティ**ウィンドウで、矢印ボタンをクリックして、 <xref:System.Windows.Forms.Control.BackColor%2A> 3 つのタブとウィンドウを表示するプロパティ。  
  
3. 選択、**カスタム**色のパレットを表示するタブ。  
  
4. 選択、 **Web**または**システム**色の定義済みの名前の一覧を表示するタブし、色を選択します。  
  
5. **プロパティ**ウィンドウで、矢印ボタンをクリックして、<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティ。  
  
6. **オープン** ダイアログ ボックスを表示するファイルを選択します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel コントロール](panel-control-windows-forms.md)
- [Panel コントロールの概要 (Windows フォーム)](panel-control-overview-windows-forms.md)
- [方法: デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する](group-controls-with-wf-panel-control-using-the-designer.md)
