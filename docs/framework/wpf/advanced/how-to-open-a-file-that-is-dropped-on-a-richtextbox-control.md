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
ms.openlocfilehash: 8ffa4c9919788060dc4524e127c181ee8282e6f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768603"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>方法: RichTextBox コントロール上にドロップしたファイルを開く
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、 <xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>、および<xref:System.Windows.Documents.FlowDocument>組み込みのドラッグ アンド ドロップ機能をすべてのコントロールがあります。 組み込みの機能により、テキスト内とコントロール間のドラッグ アンド ドロップできます。 ただし、コントロール上のファイルを削除することにより、ファイルを開く、ことはできません。 これらのコントロールは、処理済みとしても、ドラッグ アンド ドロップ イベントをマークします。 その結果、既定では、削除されたファイルを開くための機能を提供する独自のイベント ハンドラーを追加できません。  
  
 これらのコントロールでドラッグ アンド ドロップのイベントの追加の処理を追加するには、使用、<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>ドラッグ アンド ドロップのイベントをイベント ハンドラーを追加します。 設定、`handledEventsToo`パラメーターを`true`がイベント ルート上の別の要素によって処理済みとして既にマークされたルーティング イベントのために呼び出されるハンドラーを指定します。  
  
> [!TIP]
>  組み込みのドラッグ アンド ドロップ機能を置き換えることができます<xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>、および<xref:System.Windows.Documents.FlowDocument>をドラッグ アンド ドロップのイベントのプレビュー バージョンを処理し、プレビュー イベントを処理済みとしてマークします。 ただし、組み込みのドラッグ アンド ドロップ機能を無効になります、これは推奨されません。  
  
## <a name="example"></a>例  
 次の例では、ハンドラーを追加する方法、<xref:System.Windows.DragDrop.DragOver>と<xref:System.Windows.DragDrop.Drop>上のイベントを<xref:System.Windows.Controls.RichTextBox>します。 この例では、<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>メソッドとセット、`handledEventsToo`パラメーターを`true`場合でも、イベント ハンドラーが呼び出されるように、<xref:System.Windows.Controls.RichTextBox>これらのイベントを処理済みとしてマークします。 イベント ハンドラーのコードが上にドロップしたをテキスト ファイルを開く機能を追加、<xref:System.Windows.Controls.RichTextBox>します。  
  
 この例をテストするには、Windows エクスプ ローラーからテキスト ファイルまたはリッチ テキスト形式の (式 RTF) ファイルをドラッグ、<xref:System.Windows.Controls.RichTextBox>します。 ファイルを開くには、<xref:System.Windows.Controls.RichTextBox>します。 削除する前に、SHIFT キーを押した場合、ファイル、ファイルは、プレーン テキストとして開きます。  
  
 [!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
