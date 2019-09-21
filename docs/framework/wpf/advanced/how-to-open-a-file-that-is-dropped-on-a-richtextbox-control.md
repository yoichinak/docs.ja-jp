---
title: '方法: RichTextBox コントロール上にドロップしたファイルを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: 408d48856362fa8a77a44e2cc97cb2d5ff608dcf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046352"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>方法: RichTextBox コントロール上にドロップしたファイルを開く

で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、 <xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>、および<xref:System.Windows.Documents.FlowDocument>の各コントロールには、ドラッグアンドドロップ機能が組み込まれています。 組み込み機能を使用すると、コントロール内およびコントロール間でテキストをドラッグアンドドロップできます。 ただし、コントロール上のファイルを削除することによってファイルを開くことはできません。 また、これらのコントロールは、ドラッグアンドドロップイベントを処理済みとしてマークします。 その結果、既定では、削除されたファイルを開く機能を提供するための独自のイベントハンドラーを追加することはできません。

これらのコントロールでドラッグアンドドロップイベントの処理を追加するには、 <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>メソッドを使用して、ドラッグアンドドロップイベントのイベントハンドラーを追加します。 イベントルート`handledEventsToo`上の`true`別の要素によって既に処理済みとしてマークされているルーティングイベントに対して、指定したハンドラーが呼び出されるようにするには、パラメーターをに設定します。

> [!TIP]
> ドラッグアンドドロップイベントのプレビューバージョンを処理し、プレビューイベントを<xref:System.Windows.Controls.TextBox>処理<xref:System.Windows.Controls.RichTextBox>済みと<xref:System.Windows.Documents.FlowDocument>してマークすることによって、、、の組み込みのドラッグアンドドロップ機能を置き換えることができます。 ただし、これにより、組み込みのドラッグアンドドロップ機能が無効になるため、推奨されません。

## <a name="example"></a>例

次の例は、に<xref:System.Windows.DragDrop.DragOver> <xref:System.Windows.Controls.RichTextBox>イベントと<xref:System.Windows.DragDrop.Drop>イベントのハンドラーを追加する方法を示しています。 この例では<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> 、メソッドを使用`handledEventsToo`し、 `true`パラメーターをに設定して、がこれらのイベント<xref:System.Windows.Controls.RichTextBox>を処理済みとしてマークしている場合でも、イベントハンドラーが呼び出されるようにします。 イベントハンドラーのコードは、 <xref:System.Windows.Controls.RichTextBox>にドロップされたテキストファイルを開くための機能を追加します。

この例をテストするには、Windows エクスプローラーからに<xref:System.Windows.Controls.RichTextBox>テキストファイルまたはリッチテキスト形式 (RTF) ファイルをドラッグします。 ファイルはで<xref:System.Windows.Controls.RichTextBox>開かれます。 ファイルを削除する前に SHIFT キーを押すと、ファイルはプレーンテキストとして開かれます。

[!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]

[!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
[!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
