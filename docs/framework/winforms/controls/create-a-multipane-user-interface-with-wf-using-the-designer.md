---
title: '方法: デザイナーを使用して Windows フォームでマルチペイン ユーザー インターフェイスを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: f96124f7d97e733b1f0e2559320ce2e09ba5ff21
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039953"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>方法: デザイナーを使用して Windows フォームでマルチペイン ユーザー インターフェイスを作成する
次の手順では、Microsoft Outlook で使用されているものと同様のマルチペインユーザーインターフェイスを作成します。これは、**フォルダー**リスト、**メッセージ**ペイン、および**プレビュー**ウィンドウで使用します。 この配置は、フォームを使用してドッキングコントロールを主することで実現されます。

 コントロールをドッキングすると、コントロールが固定されている親コンテナーの端が決まります。 したがって<xref:System.Windows.Forms.SplitContainer.Dock%2A> 、プロパティをに<xref:System.Windows.Forms.DockStyle.Right>設定すると、コントロールの右端が親コントロールの右端にドッキングされます。 さらに、ドッキングしたコントロールの端は、コンテナーコントロールの端に合わせて変更されます。 プロパティの<xref:System.Windows.Forms.SplitContainer.Dock%2A>動作の詳細については、 [「方法:Windows フォーム](how-to-dock-controls-on-windows-forms.md)にコントロールをドッキングします。

 この手順では<xref:System.Windows.Forms.SplitContainer> 、アプリケーションが Microsoft Outlook を模倣するように機能を追加するのではなく、フォーム上のと他のコントロールを配置する方法に焦点を当てます。

 このユーザーインターフェイスを作成するには、すべてのコントロールを<xref:System.Windows.Forms.SplitContainer>コントロール内に配置し<xref:System.Windows.Forms.TreeView>ます。コントロールには、左側のパネルにコントロールが含まれています。 コントロールの<xref:System.Windows.Forms.SplitContainer>右側のパネルには、コントロールの上<xref:System.Windows.Forms.SplitContainer> <xref:System.Windows.Forms.RichTextBox>にコントロールを<xref:System.Windows.Forms.ListView>持つ2つ目のコントロールが含まれています。 これら<xref:System.Windows.Forms.SplitContainer>のコントロールを使用すると、フォーム上の他のコントロールのサイズを個別に変更できます。 この手順の手法を調整して、独自のカスタムユーザーインターフェイスを作成することができます。

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>デザイン時に Outlook スタイルのユーザーインターフェイスを作成するには

1. 新しい Windows アプリケーションプロジェクトを作成します ([**ファイル** > ] [**新しい** > **プロジェクト** > ] **[ビジュアルC# ]** または**Visual Basic** > **クラシックデスクトップ** > ) **Windows フォームアプリケーション**)。

2. コントロールを<xref:System.Windows.Forms.SplitContainer> **[ツールボックス]** からフォームにドラッグします。 **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。

3. コントロールを<xref:System.Windows.Forms.TreeView> **[ツールボックス]** から<xref:System.Windows.Forms.SplitContainer>コントロールの左側のパネルにドラッグします。 **[プロパティ]** ウィンドウで、下<xref:System.Windows.Forms.SplitContainer.Dock%2A>矢印がクリックされたときに表示される値エディターで左側のパネルをクリックして、プロパティをに<xref:System.Windows.Forms.DockStyle.Left>設定します。

4. <xref:System.Windows.Forms.SplitContainer> **ツールボックス**から別のコントロールをドラッグし、フォームに追加した<xref:System.Windows.Forms.SplitContainer>コントロールの右側のパネルに配置します。 **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.SplitContainer.Dock%2A> <xref:System.Windows.Forms.SplitContainer.Orientation%2A>プロパティをに<xref:System.Windows.Forms.DockStyle.Fill>設定し、プロパティ<xref:System.Windows.Forms.Orientation.Horizontal>をに設定します。

5. フォームに<xref:System.Windows.Forms.ListView>追加した2つ目<xref:System.Windows.Forms.SplitContainer>のコントロールの上のパネルに、**ツールボックス**からコントロールをドラッグします。 <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティの <xref:System.Windows.Forms.ListView> コントロールを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。

6. <xref:System.Windows.Forms.RichTextBox> **ツールボックス**からコントロールを2番目<xref:System.Windows.Forms.SplitContainer>のコントロールの下のパネルにドラッグします。 <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティの <xref:System.Windows.Forms.RichTextBox> コントロールを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。

     この時点で、F5 キーを押してアプリケーションを実行すると、Microsoft Outlook のような3部構成のユーザーインターフェイスがフォームに表示されます。

    > [!NOTE]
    >  <xref:System.Windows.Forms.SplitContainer>コントロール内のいずれかのスプリッターの上にマウスポインターを置くと、内部ディメンションのサイズを変更できます。

アプリケーション開発のこの時点で、洗練されたユーザーインターフェイスを作成しました。 次の手順では、アプリケーション自体のプログラミングに進みます。たとえば、 <xref:System.Windows.Forms.TreeView>コントロールと<xref:System.Windows.Forms.ListView>コントロールを何らかの種類のデータソースに接続します。 コントロールをデータに接続する方法の詳細については、「[データバインディングと Windows フォーム](../data-binding-and-windows-forms.md)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer コントロール](splitcontainer-control-windows-forms.md)
