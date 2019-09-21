---
title: 'チュートリアル: 設計時に Windows フォームで新しい WPF コンテンツを作成'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e5112aa0b025648ce68a93f0f3da026ec99fe89
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987144"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>チュートリアル: デザイン時に Windows フォームに新しい WPF コンテンツを作成する

この記事では、Windows フォームベースのアプリケーションで使用するための Windows Presentation Foundation (WPF) コントロールを作成する方法について説明します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには Visual Studio が必要です。

## <a name="create-the-project"></a>プロジェクトの作成

Visual Studio を開き、`HostingWpf` という新しい **Windows フォーム アプリ (.NET Framework)** プロジェクトを Visual Basic または Visual C# で作成します。

> [!NOTE]
> WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。

## <a name="create-a-new-wpf-control"></a>新しい WPF コントロールを作成する

新しい WPF コントロールを作成し、プロジェクトに追加するのは、プロジェクトへの他の項目の追加と同じくらい簡単です。 Windows フォームデザイナーは、*複合コントロール*または*ユーザーコントロール*という名前の特定の種類のコントロールで動作します。 WPF ユーザー コントロールの詳細については、「<xref:System.Windows.Controls.UserControl>」を参照してください。

> [!NOTE]
> WPF の <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> の種類は、同じ <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType> という名前を持つ、Windows フォームで提供されるユーザー コントロールの種類とは区別されます。

新しい WPF コントロールを作成するには:

1. **ソリューションエクスプローラー**で、新しい**WPF ユーザーコントロールライブラリ (.NET Framework)** プロジェクトをソリューションに追加します。 このコントロール ライブラリの既定の名前である `WpfControlLibrary1` を使用します。 既定のコントロールの名前は `UserControl1.xaml` です。

   新しいコントロールを追加すると、次のような効果があります。

   - ファイル UserControl1.xaml が追加されます。

   - UserControl1.xaml.cs ファイル (または UserControl1) が追加されます。 このファイルには、イベント ハンドラーとその他の実装のための分離コードが含まれています。

   - WPF アセンブリへの参照が追加されます。

   - UserControl1 ファイルは、Visual Studio の WPF デザイナーで開きます。

2. デザイン ビューで `UserControl1` が選択されていることを確認します。

3. **[プロパティ]** ウィンドウで、プロパティ<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティの値を**200**に設定します。

4. **[ツールボックス]** からコントロール<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>をデザイン画面にドラッグします。

5. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Controls.TextBox.Text%2A>プロパティの値を ホストされた **[コンテンツ]** に設定します。

   > [!NOTE]
   > 一般的には、もう少し高度な WPF コンテンツをホストしてください。 ここでは、説明する目的でのみ <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> コントロールを使用しています。

6. プロジェクトをビルドします。

## <a name="add-a-wpf-control-to-a-windows-form"></a>WPF コントロールを Windows フォームに追加する

新しい WPF コントロールは、フォームで使用可能な状態です。 Windows フォームは、 <xref:System.Windows.Forms.Integration.ElementHost>コントロールを使用して WPF コンテンツをホストします。

WPF コントロールを Windows フォームに追加するには、次のようにします。

1. Windows フォーム デザイナーで `Form1` を開きます。

2. **ツールボックス**で、 **[WPFUserControlLibrary WPF User Controls]** というラベルのタブを探します。

3. `UserControl1` のインスタンスをフォームにドラッグします。

    - WPF コントロールをホストするためのフォームの上に、<xref:System.Windows.Forms.Integration.ElementHost> コントロールが自動的に作成されます。

    - <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> `elementHost1`このコントロールにはという名前が付けられ、[プロパティ] ウィンドウで、プロパティが UserControl1 に設定されていることを確認できます。 <xref:System.Windows.Forms.Integration.ElementHost>

    - WPF アセンブリへの参照がプロジェクトに追加されます。

    - `elementHost1` コントロールに、使用可能なホスティング オプションを示すスマート タグ パネルがあります。

4. **[エンティティタスク]** スマートタグパネルで、 **[親コンテナーにドッキング]** する を選択します。

5. **F5** キーを押してアプリケーションをビルドし、実行します。

## <a name="next-steps"></a>次の手順

Windows フォームと WPF は異なるテクノロジですが、密接に相互運用するよう設計されています。 アプリケーションの外観と動作を充実させるには、次の操作を実行します。

- WPF ページで Windows フォーム コントロールをホストします。 詳細については、「[チュートリアル:WPF での Windows フォーム コントロールのホスト](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)を参照してください。

- WPF コンテンツに Windows フォームの視覚スタイルを適用します。 詳細については、「[方法 :ハイブリッドアプリケーション](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)で視覚スタイルを有効にします。

- WPF コンテンツのスタイルを変更します。 詳細については、「[チュートリアル:WPF コンテンツ](walkthrough-styling-wpf-content.md)のスタイルを設定します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移行と相互運用性](../../wpf/advanced/migration-and-interoperability.md)
- [WPF コントロールの使用](using-wpf-controls.md)
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
