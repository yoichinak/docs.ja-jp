---
title: 'チュートリアル: Windows フォーム コントロールのスマート タグを使用した共通タスクの実行'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 2805ebc66be5908c333e9a5db41076518ad77c1a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705858"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>チュートリアル: Windows フォーム コントロールのスマート タグを使用した共通タスクの実行
Windows フォーム アプリケーションのフォームとコントロールを作成するときは、繰り返し実行する多くのタスクを使用します。 これらは、発生する、一般的に実行されるタスクの一部を示します。  
  
-   追加またはでタブを削除する、<xref:System.Windows.Forms.TabControl>します。  
  
-   コントロールは、その親にドッキングします。  
  
-   向きの変更、<xref:System.Windows.Forms.SplitContainer>コントロール。  
  
 開発のスピード、多くのコントロールは、デザイン時に 1 つのジェスチャで上記のような一般的なタスクを実行するための状況依存のメニューにはスマート タグを提供します。 これらのタスクが呼び出されます*スマート タグの動詞*します。  
  
 スマート タグは、有効期間にわたって、デザイナーでコントロールのインスタンスに接続されたままし、常に利用します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   スマート タグを使用します。  
  
-   有効にして、スマート タグを無効化  
  
 終了すると、これらの重要なレイアウト機能が果たす役割について理解できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  "SmartTagsExample"と呼ばれる Windows ベースのアプリケーション プロジェクトを作成する (**ファイル** > **新規** > **プロジェクト** >  **Visual c#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォーム アプリケーション**)。  
  
2.  フォームを選択、 **Windows フォーム デザイナー**します。  
  
## <a name="using-smart-tags"></a>スマート タグを使用します。  
 スマート タグは、提供するコントロールのデザイン時に常に使用できます。  
  
#### <a name="to-use-smart-tags"></a>スマート タグを使用するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TabControl>から、**ツールボックス**フォームにします。 スマート タグ グリフに注意してください (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) のサイド バイ サイドで表示される、<xref:System.Windows.Forms.TabControl>します。  
  
2.  スマート タグ グリフをクリックします。 グリフの横に表示されるショートカット メニューで、選択、**タブの追加**項目。 新しいタブ ページが追加されたことを確認、<xref:System.Windows.Forms.TabControl>します。  
  
3.  <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。  
  
4.  スマート タグ グリフをクリックします。 グリフの横に表示されるショートカット メニューで、選択、**列の追加**項目。 新しい列が追加されたことを確認、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
5.  <xref:System.Windows.Forms.SplitContainer> ツールボックス **から** コントロールをフォームにドラッグします。  
  
6.  スマート タグ グリフをクリックします。 グリフの横に表示されるショートカット メニューで、選択、**水平分割の向き**項目。 観察、<xref:System.Windows.Forms.SplitContainer>コントロールのスプリッター バーが水平方向します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- [チュートリアル: Windows フォーム コンポーネントにスマート タグの追加](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))
