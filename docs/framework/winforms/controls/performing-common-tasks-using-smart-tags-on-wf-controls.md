---
title: 'チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07fb43a711ae8b1e2e375b17b136c07f35b1cf39
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459572"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>チュートリアル: スマートタグを使用した一般的なタスクの実行

Windows フォームアプリケーションのフォームとコントロールを構築する際には、繰り返し実行する多くのタスクがあります。 次に、一般的に実行されるタスクをいくつか示します。

- <xref:System.Windows.Forms.TabControl>のタブを追加または削除する。

- コントロールをその親にドッキングします。

- <xref:System.Windows.Forms.SplitContainer> コントロールの向きを変更する。

開発を高速化するために、多くのコントロールにスマートタグが用意されています。これは、デザイン時に1つのジェスチャでこのような一般的なタスクを実行できるようにする、状況依存のメニューです。 これらのタスクは*スマートタグ動詞*と呼ばれます。

スマートタグは、デザイナーの有効期間中はコントロールインスタンスにアタッチされたままであり、常に使用できます。

## <a name="create-the-project"></a>プロジェクトの作成

最初にプロジェクトを作成し、フォームを設定します。

1. Visual Studio で、 **SmartTagsExample**という名前の Windows ベースのアプリケーションプロジェクトを作成します。

2. **Windows フォームデザイナー**でフォームを選択します。

## <a name="use-smart-tags"></a>スマートタグを使用する

スマートタグは、デザイン時に、それらを提供するコントロールで常に使用できます。

1. **[ツールボックス]** から <xref:System.Windows.Forms.TabControl> をフォームにドラッグします。 <xref:System.Windows.Forms.TabControl>の横に表示されるスマートタググリフ (![スマートタググリフ](./media/vs-winformsmttagglyph.gif)) に注意してください。

2. スマートタググリフをクリックします。 グリフの横に表示されるショートカットメニューで、 **[タブの追加]** 項目を選択します。 新しいタブページが <xref:System.Windows.Forms.TabControl>に追加されていることを確認します。

3. <xref:System.Windows.Forms.TableLayoutPanel> ツールボックス **から** コントロールをフォームにドラッグします。

4. スマートタググリフをクリックします。 グリフの横に表示されるショートカットメニューで、 **[列の追加]** 項目を選択します。 新しい列が <xref:System.Windows.Forms.TableLayoutPanel> コントロールに追加されていることを確認します。

5. <xref:System.Windows.Forms.SplitContainer> ツールボックス **から** コントロールをフォームにドラッグします。

6. スマートタググリフをクリックします。 グリフの横に表示されるショートカットメニューで、 **[横スプリッターの方向]** 項目を選択します。 <xref:System.Windows.Forms.SplitContainer> コントロールのスプリッターバーが水平方向に配置されていることを確認します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
