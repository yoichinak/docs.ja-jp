---
title: '方法: デザイナーを使用して Windows フォームでマルチペイン ユーザー インターフェイスを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 9f3350e32c0fbff58678052d26be954d30d512a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011516"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>方法: デザイナーを使用して Windows フォームでマルチペイン ユーザー インターフェイスを作成する
Microsoft Outlook で使用される次のようなマルチペイン ユーザー インターフェイスを作成する次の手順で、**フォルダー**  ボックスの一覧を**メッセージ**ウィンドウで、および**プレビュー**ウィンドウ。 この配置は、主に、コントロールをフォームにドッキングして実現されます。  
  
 コントロールをドッキングするときに、親コンテナーの端にコントロールを固定を決定します。 そのため、設定した場合、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Right>コントロールの右端が親コントロールの右端にドッキングされます。 さらに、ドッキングされたコントロールの端は、コンテナー コントロールの一致するようにサイズ変更します。 方法の詳細については<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを参照してください[方法。Windows フォーム上のコントロールをドッキング](how-to-dock-controls-on-windows-forms.md)します。  
  
 配置でこの手順に重点を置いています、<xref:System.Windows.Forms.SplitContainer>とその他のコントロール、フォームではなく、アプリケーションを Microsoft Outlook を模倣する機能を追加します。  
  
 内のすべてのコントロールを配置するこのユーザー インターフェイスを作成する、<xref:System.Windows.Forms.SplitContainer>を格納する、<xref:System.Windows.Forms.TreeView>左側のパネルでコントロール。 右側のパネル、<xref:System.Windows.Forms.SplitContainer>コントロールには、2 つ目が含まれている<xref:System.Windows.Forms.SplitContainer>コントロールを<xref:System.Windows.Forms.ListView>コントロール上を<xref:System.Windows.Forms.RichTextBox>コントロール。 これら<xref:System.Windows.Forms.SplitContainer>コントロールがフォーム上の他のコントロールの独立したサイズ変更を有効にします。 独自のカスタム ユーザー インターフェイスを作成するには、この手順で手法を適用できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>デザイン時に Outlook のようなユーザー インターフェイスを作成するには  
  
1. 新しい Windows アプリケーション プロジェクトを作成 (**ファイル** > **新規** > **プロジェクト** > **Visual c#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォーム アプリケーション**)。  
  
2. ドラッグ、<xref:System.Windows.Forms.SplitContainer>コントロールから、**ツールボックス**をフォームにします。 **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。  
  
3. ドラッグ、<xref:System.Windows.Forms.TreeView>コントロールから、**ツールボックス**の左側のパネルに、<xref:System.Windows.Forms.SplitContainer>コントロール。 **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Left>を示す下向きの矢印がクリックされたときの値エディターで、左側のパネルをクリックします。  
  
4. もう 1 つドラッグ<xref:System.Windows.Forms.SplitContainer>コントロールから、**ツールボックス**; の右側のパネルに配置、<xref:System.Windows.Forms.SplitContainer>をフォームに追加されたコントロール。 **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>と<xref:System.Windows.Forms.SplitContainer.Orientation%2A>プロパティを<xref:System.Windows.Forms.Orientation.Horizontal>します。  
  
5. ドラッグ、<xref:System.Windows.Forms.ListView>コントロールから、**ツールボックス**、2 つ目の上側のパネルに<xref:System.Windows.Forms.SplitContainer>をフォームに追加されたコントロール。 <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティの <xref:System.Windows.Forms.ListView> コントロールを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。  
  
6. ドラッグ、<xref:System.Windows.Forms.RichTextBox>コントロールから、**ツールボックス**、2 つ目の下部のパネルに<xref:System.Windows.Forms.SplitContainer>コントロール。 <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティの <xref:System.Windows.Forms.RichTextBox> コントロールを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。  
  
     この時点では、アプリケーションの実行に f5 キーを押すと、フォームは Microsoft Outlook のような 3 つの部分のユーザー インターフェイスを表示します。  
  
    > [!NOTE]
    >  内でスプリッターのいずれかにマウス ポインターを配置すると、<xref:System.Windows.Forms.SplitContainer>コントロール内部のディメンションのサイズを変更することができます。  
  
     この時点でアプリケーションの開発では、高度なユーザー インターフェイスを作成します。 接続することで、次の手順は、アプリケーション自体のプログラミングを進める、<xref:System.Windows.Forms.TreeView>コントロールと<xref:System.Windows.Forms.ListView>いくつかの種類のデータ ソースへのコントロール。 コントロールをデータに接続する方法の詳細については、次を参照してください。[データ連結と Windows フォーム](../data-binding-and-windows-forms.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer コントロール](splitcontainer-control-windows-forms.md)
