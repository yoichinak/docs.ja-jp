---
title: WPF アプリでのインクを収集します。
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: d2178a4cbf888baaf0ae84b03b3d463b0de658b1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645729"
---
# <a name="collect-ink"></a>インクを収集します。

[Windows Presentation Foundation](../index.md) プラットフォームでは、その機能の中核としてデジタル インクが収集されます。 このトピックでは、Windows Presentation Foundation (WPF) でのインクの収集方法について説明します。

## <a name="prerequisites"></a>必須コンポーネント

次の例を使用する、Visual Studio をインストールする必要があります最初、[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]します。 WPF のアプリケーションを作成する方法を理解することもあります。 WPF の概要については、次を参照してください。[チュートリアル。初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)します。

## <a name="use-the-inkcanvas-element"></a>InkCanvas 要素を使用します。

<xref:System.Windows.Controls.InkCanvas?displayProperty=fullName>要素は、WPF のインクを収集する最も簡単な方法を提供します。 使用して、<xref:System.Windows.Controls.InkCanvas>要素を受信し、インク入力を表示します。 インクは一般的に、スタイラスを使用して入力します。スタイラスはデジタイザーとの対話により、インク ストロークを生成します。 また、スタイラスの代わりにマウスを使用することもできます。 生成されたストロークとして表される<xref:System.Windows.Ink.Stroke>プログラムとユーザーの両方の入力、オブジェクト、およびそれらを操作できます。 <xref:System.Windows.Controls.InkCanvas>ユーザーを選択し、変更、または、既存の削除をできるように<xref:System.Windows.Ink.Stroke>します。

XAML を使用して設定できますインク コレクションの追加と簡単に、 **InkCanvas**ツリーの要素。 次の例では、追加、<xref:System.Windows.Controls.InkCanvas>既定の WPF プロジェクトは Visual Studio で作成します。

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

**InkCanvas**要素は、XAML 要素のほぼすべての種類にインク注釈機能を追加することの子要素を含めることもできます。 たとえば、テキスト要素には、手描き入力機能を追加するに単に使用するの子、 <xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

インクの画像をマークするためのサポートを追加すると、同じくらい簡単です。

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>InkCollection モード

<xref:System.Windows.Controls.InkCanvas>サポートは、さまざまな入力モードをその<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>プロパティ。

### <a name="manipulate-ink"></a>インクを操作します。

<xref:System.Windows.Controls.InkCanvas>多くのインク編集操作のサポートを提供します。 たとえば、<xref:System.Windows.Controls.InkCanvas>サポート ペンのバックアップは、消去、要素に機能を追加する追加のコードは必要ありません。

#### <a name="selection"></a>選択ツール

選択モードの設定だけでは、<xref:System.Windows.Controls.InkCanvasEditingMode>プロパティを**選択**します。

次のコードの値に基づいて編集モードの設定、 <xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

使用して、<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>インク ストロークの外観を変更するプロパティ。 たとえば、<xref:System.Windows.Ink.DrawingAttributes.Color%2A>のメンバー <xref:System.Windows.Ink.DrawingAttributes> 、表示の色を設定<xref:System.Windows.Ink.Stroke>します。

次の例では、選択したストロークの色を red に変更します。

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>プロパティは、高さ、幅、およびで作成されるストロークの色などのプロパティへのアクセスを提供する<xref:System.Windows.Controls.InkCanvas>します。 変更すると、<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>に入力されるストロークはすべて、<xref:System.Windows.Controls.InkCanvas>新しいプロパティ値で表示されます。

変更するだけでなく、<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>を指定する XAML 構文を使用する分離コード ファイルで<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>プロパティ。

次の例は、設定する方法を示します、<xref:System.Windows.Ink.DrawingAttributes.Color%2A>プロパティ。 このコードを使用するには、Visual Studio で"helloinkcanvas"新しい WPF プロジェクトを作成します。 コードに置き換えます、 *MainWindow.xaml*を次のコード ファイル。

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

次に、MainWindow クラス内のファイルのコードが次のボタン イベント ハンドラーを追加します。

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

このコードをコピーした後、キーを押して**F5** Visual Studio で、デバッガーでプログラムを実行します。

通知方法、<xref:System.Windows.Controls.StackPanel>ボタンの上に配置、<xref:System.Windows.Controls.InkCanvas>します。 ボタンの上にインクを試みると、<xref:System.Windows.Controls.InkCanvas>を収集し、ボタンの背後にある、インクをレンダリングします。 これは、ボタンの兄弟であるため、<xref:System.Windows.Controls.InkCanvas>子とは対照的です。 また、ボタンは z オーダーの上位に位置するため、インクはその背後で描画されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
