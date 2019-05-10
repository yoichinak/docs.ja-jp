---
title: '方法: デザイン時に ElementHost コントロールをコピーして貼り付ける'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 0f3367deaaec04744a3f812d7f2d08047d7eb588
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211383"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a>方法: デザイン時に ElementHost コントロールをコピーして貼り付ける

この手順では、Visual Studio で Windows フォーム上の Windows Presentation Foundation (WPF) コントロールをコピーする方法を示します。

## <a name="copy-and-paste-an-elementhost-control-at-design-time"></a>コピーして、デザイン時に ElementHost コントロールを貼り付ける

1. 新しい WPF 追加<xref:System.Windows.Controls.UserControl>を Windows フォーム プロジェクトにします。 コントロール型の既定の名前である `UserControl1.xaml` を使用します。 詳細については、「[チュートリアル:デザイン時に Windows フォームで新しい WPF コンテンツを作成する](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)します。

2. **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティの`UserControl1`に`200`します。

3. <xref:System.Windows.Controls.Control.Background%2A> プロパティの値を `Blue` に設定します。

4. プロジェクトをビルドします。

5. Windows フォーム デザイナーで `Form1` を開きます。

6. **ツールボックス**のインスタンスをドラッグ`UserControl1`フォーム上にします。

   `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。

7. `elementHost1` を選択して、CTRL + C キーを押してクリップボードにコピーします。

8. コピーしたコントロールをフォームに貼り付けるには、CTRL + V キーを押します。

   新しい<xref:System.Windows.Forms.Integration.ElementHost>という名前のコントロール`elementHost2`フォーム上に作成されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移行と相互運用性](../../wpf/advanced/migration-and-interoperability.md)
- [WPF コントロールの使用](using-wpf-controls.md)
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
