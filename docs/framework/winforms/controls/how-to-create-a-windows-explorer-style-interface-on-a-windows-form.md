---
title: '方法: Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 34a5cd735c350688d9e83003806668e213932c85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960623"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>方法: Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する
Windows Explorer は、アプリケーションのユーザーインターフェイスの一般的な選択肢であり、その準備が整っているためです。

 Windows エクスプローラーは、基本的<xref:System.Windows.Forms.TreeView>にはコントロール<xref:System.Windows.Forms.ListView>であり、別のパネルのコントロールです。 パネルはスプリッターによってサイズ変更できるようになります。 このコントロールの配置は、情報を表示および参照するために非常に効果的です。

 次の手順では、Windows エクスプローラーのようなフォームでコントロールを配置する方法について説明します。 Windows Explorer アプリケーションのファイル参照機能を追加する方法については説明しません。

## <a name="to-create-a-windows-explorer-style-windows-form"></a>Windows エクスプローラースタイルの Windows フォームを作成するには

1. 新しい Windows アプリケーションプロジェクトを作成します ([**ファイル** > ] [**新しい** > **プロジェクト** > ] **[ビジュアルC# ]** または**Visual Basic** > **クラシックデスクトップ** > ) **Windows フォームアプリケーション**)。

2. **ツールボックス**から:

    1. コントロールを<xref:System.Windows.Forms.SplitContainer>フォームにドラッグします。

    2. コントロールを<xref:System.Windows.Forms.TreeView> **SplitterPanel1** (Panel1 とマークされた<xref:System.Windows.Forms.SplitContainer>コントロールのパネル) にドラッグします。

    3. コントロールを<xref:System.Windows.Forms.ListView> **SplitterPanel2** (Panel2 とマークされた<xref:System.Windows.Forms.SplitContainer>コントロールのパネル) にドラッグします。

3. CTRL キーを押しながら3つのコントロールをすべて選択し、順番にクリックします。 <xref:System.Windows.Forms.SplitContainer>コントロールを選択するときは、パネルではなくスプリッターバーをクリックします。

    > [!NOTE]
    > **[編集]** メニューの **[すべて選択]** コマンドを使用しないでください。 その場合、次の手順で必要なプロパティは、 **[プロパティ]** ウィンドウに表示されません。

4. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。

5. F5 キーを押してアプリケーションを実行します。

     フォームには、Windows エクスプローラーと同様の2つの部分で構成されるユーザーインターフェイスが表示されます。

    > [!NOTE]
    > スプリッターをドラッグすると、パネル自体のサイズが変更されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.SplitContainer>
- [方法: Windows フォームを使用してマルチペインユーザーインターフェイスを作成する](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [方法: 分割ウィンドウでのサイズ変更および配置動作の定義](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [方法: ウィンドウを水平方向に分割する](how-to-split-a-window-horizontally.md)
- [SplitContainer コントロール](splitcontainer-control-windows-forms.md)
