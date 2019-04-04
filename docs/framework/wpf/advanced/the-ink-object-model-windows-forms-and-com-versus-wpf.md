---
title: インク オブジェクト モデル:Windows フォームおよび COM と WPF の比較
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
ms.openlocfilehash: 68003943041fe0ba405eff1236c43a8e7e9c2b71
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356833"
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>インク オブジェクト モデル:Windows フォームおよび COM と WPF の比較

デジタル インクをサポートする 3 つのプラットフォーム基本的には: タブレット PC の Windows フォームのプラットフォーム、Tablet PC の COM のプラットフォームおよび Windows Presentation Foundation (WPF) プラットフォーム。  同様のオブジェクト モデルが、オブジェクトをモデルの Windows フォームおよび COM のプラットフォームの共有、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プラットフォームは大幅に異なります。  このトピックでは、1 つのオブジェクト モデルを使用してきた開発者は、他を理解できるように、簡単に説明する違いをについて説明します。  
  
## <a name="enabling-ink-in-an-application"></a>アプリケーションでのインクを有効にします。  
 3 つすべてのプラットフォームでは、オブジェクトやタブレット ペンから入力を受信するアプリケーションを有効にするコントロールを出荷します。  Windows フォームおよび COM のプラットフォームで同梱[Microsoft.Ink.InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90))、 [Microsoft.Ink.InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))、 [Microsoft.Ink.InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90))と[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))クラス。  [Microsoft.Ink.InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90))と[Microsoft.Ink.InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))追加できるコントロールはインクを収集するアプリケーションにします。  [Microsoft.Ink.InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90))と[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))インク対応の windows とカスタム コントロールに既存のウィンドウにアタッチできます。  
  
 WPF プラットフォームには、<xref:System.Windows.Controls.InkCanvas>コントロール。  追加することができます、<xref:System.Windows.Controls.InkCanvas>アプリケーションにし、すぐにインクの収集を開始します。 <xref:System.Windows.Controls.InkCanvas>ユーザーは、コピー、選択、およびインクのサイズを変更します。  他のコントロールを追加することができます、 <xref:System.Windows.Controls.InkCanvas>、し、ユーザーが、これらのコントロールをすぎる手書きことができます。  インク対応のカスタム コントロールを作成するには追加することで、<xref:System.Windows.Controls.InkPresenter>とそのスタイラス ポイントを収集します。  
  
 次の表は、アプリケーションでのインクを有効にする方法の詳細を知りたいです。  
  
|これを行う.|WPF プラットフォームにしています.|Windows フォームや COM のプラットフォームで.|  
|-----------------|--------------------------|------------------------------------------|  
|インク対応コントロールをアプリケーションに追加します。|参照してください[インクの概要](getting-started-with-ink.md)します。|参照してください[自動要求フォーム サンプル](/windows/desktop/tablet/auto-claims-form-sample)|  
|カスタム コントロールでインクを有効にします。|参照してください[作成インク入力コントロール](creating-an-ink-input-control.md)します。|参照してください[クリップボードのサンプルをインク](/windows/desktop/tablet/ink-clipboard-sample)します。|  
  
## <a name="ink-data"></a>インク データ  
 Windows フォームおよび COM のプラットフォームに[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))、 [Microsoft.Ink.InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90))、 [Microsoft.Ink.InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))、および[Microsoft.Ink.InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90))各公開、 [Microsoft.Ink.Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))オブジェクト。 [Microsoft.Ink.Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))オブジェクトは、1 つまたは複数のデータを含む[Microsoft.Ink.Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90))オブジェクトし、共通のメソッドとプロパティを管理し、それらのストロークの操作を公開します。  [Microsoft.Ink.Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))オブジェクトが含まれています。 ストロークの有効期間を管理する、 [Microsoft.Ink.Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))オブジェクトを作成し、所有するストロークを削除します。  各[Microsoft.Ink.Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90))親内で一意の識別子を持つ[Microsoft.Ink.Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))オブジェクト。  
  
 WPF のプラットフォームで、<xref:System.Windows.Ink.Stroke?displayProperty=nameWithType>クラスを所有し、独自の有効期間を管理します。 グループ<xref:System.Windows.Ink.Stroke>でオブジェクトをまとめて収集できる、<xref:System.Windows.Ink.StrokeCollection>メソッドを提供しますの一般的なインク データ管理操作など、ヒット テスト、消去、変換、および手描き入力をシリアル化します。 A <xref:System.Windows.Ink.Stroke> 0、1 つ、以上に属することができます<xref:System.Windows.Ink.StrokeCollection>いずれかのオブジェクトは、時間を与えます。  はなく、 [Microsoft.Ink.Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))オブジェクト、<xref:System.Windows.Controls.InkCanvas>と<xref:System.Windows.Controls.InkPresenter>を含む、<xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>します。  
  
 次の図のペアは、インク データのオブジェクト モデルを比較します。  Windows フォームおよび COM のプラットフォームに、 [Microsoft.Ink.Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90))オブジェクトの有効期間の制限、 [Microsoft.Ink.Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90))オブジェクト、および個々 のストロークに属するスタイラス パケット。  2 つ以上のストロークが参照できる同じ[Microsoft.Ink.DrawingAttributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583636(v=vs.90))オブジェクト、次の図に示すようにします。  
  
 ![COM のインク オブジェクト モデルのダイアグラム&#47;Winforms します。](./media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、それぞれ<xref:System.Windows.Ink.Stroke?displayProperty=nameWithType>が共通言語ランタイム オブジェクトへの参照を持つものとして存在します。  各<xref:System.Windows.Ink.Stroke>参照、<xref:System.Windows.Input.StylusPointCollection>と<xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType>オブジェクトは、共通言語ランタイム オブジェクトでもあります。  
  
 ![WPF のインク オブジェクト モデルのダイアグラム。](./media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 次の表に一般的なタスクを実行する方法の比較、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プラットフォームと Windows フォームおよび COM のプラットフォームです。  
  
|タスク|Windows Presentation Foundation|Windows フォームおよび COM|  
|----------|-------------------------------------|---------------------------|  
|インクを保存します。|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571335(v=vs.90))|  
|インクを読み込み|作成、<xref:System.Windows.Ink.StrokeCollection>で、<xref:System.Windows.Ink.StrokeCollection.%23ctor%2A>コンス トラクター。|[Microsoft.Ink.Ink.Load](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms569609(v=vs.90))|  
|ヒット テスト|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571330(v=vs.90))|  
|インクをコピーします。|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571316(v=vs.90))|  
|インクを貼り付け|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571318(v=vs.90))|  
|ストロークのコレクションへのアクセスのカスタム プロパティ|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (プロパティが内部的に保存され、使用してアクセス<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>、 <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>、および<xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|使用[Microsoft.Ink.Ink.ExtendedProperties](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms582214(v=vs.90))|  
  
### <a name="sharing-ink-between-platforms"></a>プラットフォーム間でのインクの共有  
 プラットフォームには、インク データのさまざまなオブジェクト モデルがありますが、プラットフォーム間でデータの共有は非常に簡単にします。 次の例では、Windows フォーム アプリケーションからインクを保存し、Windows Presentation Foundation アプリケーションにインクを読み込みます。  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 次の例では、Windows Presentation Foundation アプリケーションからインクを保存し、Windows フォーム アプリケーションに、インクを読み込みます。  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>タブレット ペンからのイベント  

 [Microsoft.Ink.InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90))、 [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))、および[Microsoft.Ink.InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90))プラットフォームは Windows フォームおよび COM にイベントを受け取るときに、ユーザーペンのデータを入力します。 [Microsoft.Ink.InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90))または[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))はウィンドウやコントロールにアタッチされ、タブレット入力データによって発生したイベントにサブスクライブできます。 これらのイベントが発生するスレッドは、マウス、ペンを使用して、イベントが発生したかどうかに依存またはプログラムを使用します。 これらのイベントに関連スレッド処理の詳細については、[一般的なスレッド処理の考慮事項](/windows/desktop/tablet/general-threading-considerations)と[にイベントが起動できるスレッド](/windows/desktop/tablet/threads-on-which-an-event-can-fire)を参照してください。  
  
 Windows Presentation Foundation のプラットフォームで、<xref:System.Windows.UIElement>クラスのペン入力イベントがあります。 これは、すべてのコントロールがスタイラス イベントの完全なセットを公開していることを意味します。  スタイラス イベントがあるトンネルとバブル イベントのペアし、アプリケーションのスレッドで常に発生します。  詳細については、[ルーティング イベントの概要](routed-events-overview.md)を参照してください。  
  
 次の図は、スタイラス イベントを発生させるクラスのオブジェクト モデルを比較します。 Windows Presentation Foundation オブジェクト モデルには、バブル イベント、のみであり、トンネリング イベント対応ではありませんが表示されます。  
  
 ![WPF と Winforms のスタイラス イベントのダイアグラム。](./media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>ペン データ  
 3 つすべてのプラットフォームは、インターセプト、タブレット ペン由来するデータを操作する方法を提供します。  Windows フォームおよび COM のプラットフォームで、作成してこれは、 [Microsoft.StylusInput.RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90))、ウィンドウやコントロールをそれにアタッチしを実装するクラスを作成、 [Microsoft.StylusInput.IStylusSyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575201(v=vs.90))または[Microsoft.StylusInput.IStylusAsyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575194(v=vs.90))インターフェイス。 カスタム プラグインがプラグインのコレクションに追加し、 [Microsoft.StylusInput.RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90))します。 このオブジェクト モデルの詳細については、[StylusInput Api のアーキテクチャ](/windows/desktop/tablet/architecture-of-the-stylusinput-apis)を参照してください。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 、プラットフォーム、<xref:System.Windows.UIElement>クラスのプラグイン、同様のデザインのコレクションを公開する、 [Microsoft.StylusInput.RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90))します。  ペンのデータをインターセプトするから継承するクラスを作成<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>オブジェクトを追加して、<xref:System.Windows.UIElement.StylusPlugIns%2A>のコレクション、<xref:System.Windows.UIElement>します。 この操作の詳細については、[スタイラスからの入力のインターセプト](intercepting-input-from-the-stylus.md)を参照してください。  
  
 すべてのプラットフォームでは、スレッド プールは、スタイラス イベントを使用して、インク データを受信し、アプリケーション スレッドに送信します。  スレッドの COM および Windows プラットフォームの詳細については、[StylusInput Api に関する考慮事項をスレッド](/windows/desktop/tablet/threading-considerations-for-the-stylusinput-apis)を参照してください。  スレッドの Windows プレゼンテーション ソフトウェアの詳細については、[インク スレッド モデル](the-ink-threading-model.md)を参照してください。  
  
 次の図は、ペン スレッド プールでペンのデータを受信するクラスのオブジェクト モデルを比較します。  
  
 ![StylusPlugin モデル WPF と Winforms のダイアグラム。](./media/ink-stylusplugins.png "Ink_StylusPlugins")
