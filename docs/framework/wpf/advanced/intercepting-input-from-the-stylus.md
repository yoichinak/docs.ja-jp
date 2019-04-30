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
ms.openlocfilehash: 5c22c2862ae8b948787fd5e6ca16109aa2f52aef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031253"
---
# <a name="intercepting-input-from-the-stylus"></a>スタイラスからの入力のインターセプト
<xref:System.Windows.Input.StylusPlugIns>アーキテクチャに低レベルの制御を実装するためのメカニズムを提供する<xref:System.Windows.Input.Stylus>入力およびデジタル インクの作成<xref:System.Windows.Ink.Stroke>オブジェクト。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>クラスがカスタム動作を実装し、最適なパフォーマンスのスタイラス デバイスからのデータのストリームに適用するためのメカニズムを提供します。  
  
 このトピックは、次の内容で構成されています。  
  
- [アーキテクチャ](#Architecture)  
  
- [スタイラス プラグインを実装します。](#ImplementingStylusPlugins)  
  
- [InkCanvas にプラグインを追加します。](#AddingYourPluginToAnInkCanvas)  
  
- [まとめ](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>アーキテクチャ  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>の進化には、 [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409)で説明されている Api[へのアクセスおよび操作するペン入力](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)の[Microsoft Windows XP Tablet PC Edition のソフトウェアDevelopment Kit 1.7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409)します。  
  
 各<xref:System.Windows.UIElement>が、<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティが、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>します。 追加することができます、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>要素の<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティを操作する<xref:System.Windows.Input.StylusPoint>データが生成されます。 <xref:System.Windows.Input.StylusPoint> データを含む、システムのデジタイザーでサポートされるすべてのプロパティから成る、<xref:System.Windows.Input.StylusPoint.X%2A>と<xref:System.Windows.Input.StylusPoint.Y%2A>、データ ポイントだけでなく<xref:System.Windows.Input.StylusPoint.PressureFactor%2A>データ。  
  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>オブジェクトからのデータのストリームに直接挿入、<xref:System.Windows.Input.Stylus>デバイスを追加すると、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>を<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティ。 プラグインを追加する順序、<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクションが表示される順序を決定する<xref:System.Windows.Input.StylusPoint>データ。 など、特定のリージョンへの入力を制限するフィルター プラグインを追加してデータを書き込むときに、ジェスチャを認識するプラグインを追加し、ジェスチャを認識するプラグインは受信フィルター選択された<xref:System.Windows.Input.StylusPoint>データ。  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>スタイラス プラグインを実装します。  
 プラグインを実装する派生クラスを<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>します。 このクラスはデータのストリームからなる、<xref:System.Windows.Input.Stylus>します。 このクラスでは、値を変更することができます、<xref:System.Windows.Input.StylusPoint>データ。  
  
> [!CAUTION]
>  場合、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>をスローするか閉じて、アプリケーションは、例外が発生します。 使用するコントロールを十分にテストする必要があります、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>のみがわかっている場合に、コントロールを使用して、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>例外はスローされません。  
  
 次の例で変更することで、スタイラスからの入力を制限するプラグイン、<xref:System.Windows.Input.StylusPoint.X%2A>と<xref:System.Windows.Input.StylusPoint.Y%2A>値、<xref:System.Windows.Input.StylusPoint>からデータを受信、<xref:System.Windows.Input.Stylus>デバイス。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>InkCanvas にプラグインを追加します。  
 カスタム プラグインを使用する最も簡単な方法は、InkCanvas から派生したクラスの実装を追加するには、<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティ。  
  
 次の例では、カスタム<xref:System.Windows.Controls.InkCanvas>手描き入力をフィルター処理します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 追加する場合、`FilterInkCanvas`実行、アプリケーションを表示されます、ユーザーがストロークが完了したらインクはまでの領域に制限されています。 これは、ため、<xref:System.Windows.Controls.InkCanvas>が、<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>であるプロパティを<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>のメンバーであると、<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクション。 カスタム<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>に追加した、<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクションには、<xref:System.Windows.Input.StylusPoint>後のデータ<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>データを受信します。 結果として、<xref:System.Windows.Input.StylusPoint>ユーザーがストロークを終了するペン離した後のデータはまでフィルターされません。 ユーザーが描画と手描き入力をフィルターするに挿入する必要があります、`FilterPlugin`する前に、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>します。  
  
 次の c# コードに示しますカスタム<xref:System.Windows.Controls.InkCanvas>描画されると、手描き入力をフィルター処理します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>まとめ  
 独自の派生によって<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>クラスとそれらに挿入する<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>コレクションのデジタル インクの動作を大幅に向上することができます。 アクセスがある、<xref:System.Windows.Input.StylusPoint>ほどデータの生成をカスタマイズする機会を与える、<xref:System.Windows.Input.Stylus>入力します。 このような低レベルのアクセス権があるため、<xref:System.Windows.Input.StylusPoint>データ、アプリケーションのインクの収集と最適なパフォーマンスの表示を実装することができます。  
  
## <a name="see-also"></a>関連項目

- [高度なインク処理](advanced-ink-handling.md)
- [アクセスして、ペン入力を操作します。](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
