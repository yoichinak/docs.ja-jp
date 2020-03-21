---
title: スタイラスからの入力のインターセプト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
ms.openlocfilehash: 17cf42a9d6d94d6ea12399561af5647df3b4d8c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181918"
---
# <a name="intercepting-input-from-the-stylus"></a>スタイラスからの入力のインターセプト
この<xref:System.Windows.Input.StylusPlugIns>アーキテクチャは、入力とデジタル インク<xref:System.Windows.Input.Stylus><xref:System.Windows.Ink.Stroke>オブジェクトの作成に対して低レベルの制御を実装するためのメカニズムを提供します。 この<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>クラスは、カスタム動作を実装し、最適なパフォーマンスを得るためにスタイラス デバイスから取得したデータ ストリームに適用するためのメカニズムを提供します。  
  
 このトピックは、次の内容で構成されています。  
  
- [アーキテクチャ](#Architecture)  
  
- [スタイラス プラグインの実装](#ImplementingStylusPlugins)  
  
- [プラグインをインクキャンバスに追加する](#AddingYourPluginToAnInkCanvas)  
  
- [結論](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Architecture  
 は<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>、[ペン入力へのアクセスと操作](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))で説明されている[、StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) API の進化です。  
  
 それぞれに<xref:System.Windows.UIElement>. <xref:System.Windows.UIElement.StylusPlugIns%2A> <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 要素の<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn><xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティに を追加して、生成されるデータ<xref:System.Windows.Input.StylusPoint>を操作できます。 <xref:System.Windows.Input.StylusPoint>データは、システム・デジタイザがサポートするすべてのプロパティ(<xref:System.Windows.Input.StylusPoint.X%2A><xref:System.Windows.Input.StylusPoint.Y%2A>およびポイント・データを含む)<xref:System.Windows.Input.StylusPoint.PressureFactor%2A>とデータで構成されます。  
  
 オブジェクト<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>は、プロパティに追加するときに<xref:System.Windows.Input.Stylus>、デバイスから取得されるデータのストリーム<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>に直接挿入されます。 <xref:System.Windows.UIElement.StylusPlugIns%2A> プラグインが<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクションに追加される順序によって、データを受け取<xref:System.Windows.Input.StylusPoint>る順序が決まります。 たとえば、特定の領域への入力を制限するフィルター プラグインを追加し、ジェスチャが書かれていると認識するプラグインを追加すると、ジェスチャを認識するプラグインはフィルター処理されたデータを<xref:System.Windows.Input.StylusPoint>受け取ります。  
  
<a name="ImplementingStylusPlugins"></a>
## <a name="implementing-stylus-plug-ins"></a>スタイラス プラグインの実装  
 プラグインを実装するには、 から<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>クラスを派生させます。 このクラスは、 から入ってくるデータストリームに適用されます<xref:System.Windows.Input.Stylus>。 このクラスでは、データの値を<xref:System.Windows.Input.StylusPoint>変更できます。  
  
> [!CAUTION]
> 例外が<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>スローまたは発生した場合、アプリケーションは終了します。 を使用するコントロールを徹底的にテスト<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>し、例外をスローしないことが確実な場合<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>にのみコントロールを使用する必要があります。  
  
 次の例は、デバイスから入ってくる<xref:System.Windows.Input.StylusPoint.X%2A>データの値と 値<xref:System.Windows.Input.StylusPoint.Y%2A>を変更してスタイラス入力を<xref:System.Windows.Input.StylusPoint>制限するプラグインを<xref:System.Windows.Input.Stylus>示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>プラグインをインクキャンバスに追加する  
 カスタム プラグインを使用する最も簡単な方法は、InkCanvas から派生したクラスを実装し、プロパティに<xref:System.Windows.UIElement.StylusPlugIns%2A>追加することです。  
  
 インクをフィルター処理するカスタム<xref:System.Windows.Controls.InkCanvas>の例を次に示します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 アプリケーションに を`FilterInkCanvas`追加して実行すると、ユーザーがストロークを完了するまでインクが領域に限定されないことがわかります。 これは、<xref:System.Windows.Controls.InkCanvas>プロパティがあり<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>、既に<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn><xref:System.Windows.UIElement.StylusPlugIns%2A>コレクションのメンバーであるためです。 コレクションに<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>追加したカスタムは<xref:System.Windows.UIElement.StylusPlugIns%2A>、データを受<xref:System.Windows.Input.StylusPoint>け取<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>った後でデータを受信します。 その結果、ユーザーが<xref:System.Windows.Input.StylusPoint>ペンを持ち上げてストロークを終了するまで、データはフィルター処理されません。 ユーザーが描画するインクをフィルター処理するには、 の`FilterPlugin`前に を<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>挿入する必要があります。  
  
 次の C# コードは、<xref:System.Windows.Controls.InkCanvas>描画時にインクをフィルター処理するカスタムを示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>まとめ  
 独自<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>のクラスを派生させ、コレクションに<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>挿入することで、デジタル インクの動作を大幅に向上させることができます。 生成される<xref:System.Windows.Input.StylusPoint>データにアクセスして、入力をカスタマイズできます<xref:System.Windows.Input.Stylus>。 <xref:System.Windows.Input.StylusPoint>データへの低レベルのアクセスが可能なため、アプリケーションに最適なパフォーマンスでインクの収集とレンダリングを実装できます。  
  
## <a name="see-also"></a>関連項目

- [高度なインク処理](advanced-ink-handling.md)
- [ペン入力へのアクセスと操作](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
