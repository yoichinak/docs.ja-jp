---
title: ToolBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: 7b39c8e3dca88e968b43ba5ff14794e2e77247d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174812"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar コントロールの概要 (Windows フォーム)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォーム <xref:System.Windows.Forms.ToolBar> コントロールは、コマンドをアクティブ化するドロップダウン メニューとビットマップのボタンの行を表示するコントロール バーとしてフォームを使用します。 そのため、ツールバー ボタンをクリックすることは、メニュー コマンドを選択することと同じです。 ボタンは、プッシュ ボタン、ドロップダウン メニュー、または区切りとして表示して機能するように構成できます。 通常、ツールバーには、アプリケーションのメニュー構造の項目に対応するボタンとメニューが含まれ、アプリケーションで最も頻繁に使用される関数やコマンドにすばやくアクセスできます。  
  
## <a name="working-with-the-toolbar-control"></a>ToolBar コントロールの操作  
 A<xref:System.Windows.Forms.ToolBar>コントロールは通常に沿って「ドッキング」、その親ウィンドウの上部がウィンドウの左右のどこにでもドッキングできます。 ツール バー ボタンをマウス ポインターでポイントすると、ツールヒントが表示されます。 ツールヒントは、ボタンやメニューの目的を簡単に説明する小さなポップアップ ウィンドウです。 ツールヒントを表示する、<xref:System.Windows.Forms.ToolBar.ShowToolTips%2A>にプロパティを設定する必要があります`true`します。  
  
> [!NOTE]
>  特定のアプリケーション機能のコントロールは、アプリケーション ウィンドウの上に "フローティング" して位置変更できるツールバーとよく似ています。 Windows フォームのツール バー コントロールでは、このような操作を実行できません。  
  
 ときに、<xref:System.Windows.Forms.ToolBar.Appearance%2A>プロパティに設定されて<xref:System.Windows.Forms.ToolBarAppearance>、立体的な 3 次元に、ツールバーのボタンが表示されます。 設定することができます、<xref:System.Windows.Forms.ToolBar.Appearance%2A>プロパティ ツールバーの<xref:System.Windows.Forms.ToolBarAppearance>ツールバーとそのボタンのフラットな外観を提供します。 フラットなボタンにマウス ポインターを置くと、ボタンは 3 次元表示に変わります。 ツール バー ボタンは、区切りを使用すると論理グループに分けることができます。 区切り記号がツール バー ボタンで、<xref:System.Windows.Forms.ToolBarButton.Style%2A>プロパティに設定<xref:System.Windows.Forms.ToolBarButtonStyle>します。 区切りは、ツール バー上の空スペースとして表示されます。 ツール バーはフラットに表示され、ボタンの区切りは、ボタンの間にスペースを入れて表示されるのではなく線として表示されます。  
  
 <xref:System.Windows.Forms.ToolBar>コントロールでは、追加することでツールバーを作成できます。<xref:System.Windows.Forms.Button>オブジェクトを、<xref:System.Windows.Forms.ToolBar.Buttons%2A>コレクション。 コレクション エディターを使用してボタンを追加することができます、<xref:System.Windows.Forms.ToolBar>コントロール; 各<xref:System.Windows.Forms.Button>オブジェクトがテキストまたはイメージが割り当てられて、両方を割り当てることができます。 イメージは、関連付けられた [ImageList](imagelist-component-windows-forms.md) コンポーネントから取得されます。 実行時に、追加または削除 ボタンから、<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>を使用して、<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A>と<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A>メソッド。 ボタンを<xref:System.Windows.Forms.ToolBar>、コードを追加、<xref:System.Windows.Forms.ToolBar.ButtonClick>のイベント、<xref:System.Windows.Forms.ToolBar>を使用して、<xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A>のプロパティ、<xref:System.Windows.Forms.ToolBarButtonClickEventArgs>クラスのどのボタンがクリックしてされたかを判断します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolBar>
- [ToolBar コントロール](toolbar-control-windows-forms.md)
- [方法: ツール バー コントロールにボタンを追加します。](how-to-add-buttons-to-a-toolbar-control.md)
- [方法: ツール バー ボタンのアイコンを定義します。](how-to-define-an-icon-for-a-toolbar-button.md)
- [方法: ツール バー ボタンのメニュー イベントのトリガー](how-to-trigger-menu-events-for-toolbar-buttons.md)
