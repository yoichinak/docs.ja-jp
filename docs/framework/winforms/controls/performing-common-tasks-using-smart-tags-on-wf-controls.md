---
title: 'チュートリアル: Windows フォーム コントロールのスマート タグを使用した共通タスクの実行'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015758"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>チュートリアル: スマートタグを使用した一般的なタスクの実行

Windows フォームアプリケーションのフォームとコントロールを構築する際には、繰り返し実行する多くのタスクがあります。 次に、一般的に実行されるタスクをいくつか示します。

- でのタブの追加または<xref:System.Windows.Forms.TabControl>削除。

- コントロールをその親にドッキングします。

- <xref:System.Windows.Forms.SplitContainer>コントロールの向きを変更する。

開発を高速化するために、多くのコントロールにスマートタグが用意されています。これは、デザイン時に1つのジェスチャでこのような一般的なタスクを実行できるようにする、状況依存のメニューです。 これらのタスクは*スマートタグ動詞*と呼ばれます。

スマートタグは、デザイナーの有効期間中はコントロールインスタンスにアタッチされたままであり、常に使用できます。

## <a name="create-the-project"></a>プロジェクトの作成

最初にプロジェクトを作成し、フォームを設定します。

1. Visual Studio で、 **SmartTagsExample**という名前の Windows ベースのアプリケーションプロジェクトを作成します。

2. **Windows フォームデザイナー**でフォームを選択します。

## <a name="use-smart-tags"></a>スマートタグを使用する

スマートタグは、デザイン時に、それらを提供するコントロールで常に使用できます。

1. <xref:System.Windows.Forms.TabControl> **ツールボックス**からフォームにをドラッグします。 の横![に表示](./media/vs-winformsmttagglyph.gif)されるスマートタググリフ (スマートタググリフ) に注意してください。<xref:System.Windows.Forms.TabControl>

2. スマートタググリフをクリックします。 グリフの横に表示されるショートカットメニューで、 **[タブの追加]** 項目を選択します。 新しいタブページがに<xref:System.Windows.Forms.TabControl>追加されていることを確認します。

3. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。

4. スマートタググリフをクリックします。 グリフの横に表示されるショートカットメニューで、 **[列の追加]** 項目を選択します。 <xref:System.Windows.Forms.TableLayoutPanel>コントロールに新しい列が追加されていることを確認します。

5. <xref:System.Windows.Forms.SplitContainer> ツールボックス **から** コントロールをフォームにドラッグします。

6. スマートタググリフをクリックします。 グリフの横に表示されるショートカットメニューで、 **[横スプリッターの方向]** 項目を選択します。 <xref:System.Windows.Forms.SplitContainer>コントロールのスプリッターバーが水平方向に配置されていることを確認します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
