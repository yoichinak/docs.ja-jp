---
title: 'チュートリアル: Windows フォーム コントロールのスマート タグを使用した共通タスクの実行'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 1cc854d735ba88a301d6e2f6a83fe5c8bf881380
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211417"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>チュートリアル: Windows フォーム コントロールのスマート タグを使用した共通タスクの実行

Windows フォーム アプリケーションのフォームとコントロールを作成するときは、繰り返し実行する多くのタスクを使用します。 これらは、発生する、一般的に実行されるタスクの一部を示します。

- 追加またはでタブを削除する、<xref:System.Windows.Forms.TabControl>します。

- コントロールは、その親にドッキングします。

- 向きの変更、<xref:System.Windows.Forms.SplitContainer>コントロール。

開発のスピード、多くのコントロールは、デザイン時に 1 つのジェスチャで上記のような一般的なタスクを実行するための状況依存のメニューにはスマート タグを提供します。 これらのタスクが呼び出されます*スマート タグの動詞*します。

スマート タグは、有効期間にわたって、デザイナーでコントロールのインスタンスに接続されたままし、常に利用します。

このチュートリアルでは、以下のタスクを行います。

- Windows フォーム プロジェクトの作成

- スマート タグを使用します。

- 有効にして、スマート タグを無効化

終了すると、これらの重要なレイアウト機能が果たす役割について理解できます。

## <a name="create-the-project"></a>プロジェクトの作成

最初にプロジェクトを作成し、フォームを設定します。

1. Visual Studio で、"SmartTagsExample"と呼ばれる Windows ベースのアプリケーション プロジェクトを作成します (**ファイル** > **新規** > **プロジェクト** >  **Visual C#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォームアプリケーション**)。

2. フォームを選択、 **Windows フォーム デザイナー**します。

## <a name="use-smart-tags"></a>スマート タグを使用します。

スマート タグは、提供するコントロールのデザイン時に常に使用できます。

1. ドラッグ、<xref:System.Windows.Forms.TabControl>から、**ツールボックス**フォームにします。 スマート タグ グリフに注意してください (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) のサイド バイ サイドで表示される、<xref:System.Windows.Forms.TabControl>します。

2. スマート タグ グリフをクリックします。 グリフの横に表示されるショートカット メニューで、選択、**タブの追加**項目。 新しいタブ ページが追加されたことを確認、<xref:System.Windows.Forms.TabControl>します。

3. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。

4. スマート タグ グリフをクリックします。 グリフの横に表示されるショートカット メニューで、選択、**列の追加**項目。 新しい列が追加されたことを確認、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。

5. <xref:System.Windows.Forms.SplitContainer> ツールボックス **から** コントロールをフォームにドラッグします。

6. スマート タグ グリフをクリックします。 グリフの横に表示されるショートカット メニューで、選択、**水平分割の向き**項目。 観察、<xref:System.Windows.Forms.SplitContainer>コントロールのスプリッター バーが水平方向します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- [チュートリアル: Windows フォーム コンポーネントにスマート タグの追加](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))
