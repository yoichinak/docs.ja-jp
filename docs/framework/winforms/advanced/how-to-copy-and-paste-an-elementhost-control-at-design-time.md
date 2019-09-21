---
title: '方法: デザイン時に ElementHost コントロールをコピーして貼り付ける'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666180"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>方法: コントロールのコピーと貼り付け

この手順では、Visual Studio の Windows フォームで Windows Presentation Foundation (WPF) コントロールをコピーする方法について説明します。

1. Visual Studio で、Windows フォームプロジェクトに新しい<xref:System.Windows.Controls.UserControl> WPF を追加します。 コントロール型の既定の名前である `UserControl1.xaml` を使用します。 詳細については、「[チュートリアル:デザイン時](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)に WINDOWS フォームに新しい WPF コンテンツを作成する。

2. **[プロパティ]** ウィンドウで、の<xref:System.Windows.FrameworkElement.Width%2A> `UserControl1`プロパティと<xref:System.Windows.FrameworkElement.Height%2A>プロパティの値を**200**に設定します。

3. <xref:System.Windows.Controls.Control.Background%2A>プロパティの値を**Blue**に設定します。

4. プロジェクトをビルドします。

5. Windows フォーム デザイナーで `Form1` を開きます。

6. **ツールボックス**から、の`UserControl1`インスタンスをフォームにドラッグします。

   `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。

7. を選択した状態で、 **Ctrl**+C キーを押してクリップボードにコピーします。 `elementHost1`

8. **Ctrl**+**V**キーを押して、コピーしたコントロールをフォームに貼り付けます。

   という<xref:System.Windows.Forms.Integration.ElementHost>名前`elementHost2`の新しいコントロールがフォーム上に作成されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移行と相互運用性](../../wpf/advanced/migration-and-interoperability.md)
- [WPF コントロールの使用](using-wpf-controls.md)
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
