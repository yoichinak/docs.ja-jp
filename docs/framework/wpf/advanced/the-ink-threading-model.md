---
title: インク スレッド モデル
ms.date: 03/30/2017
helpviewer_keywords:
- application user interface thread [WPF]
- stylus plug-in
- ink threading model [WPF]
- ink [WPF], rendering
- pen thread [WPF]
- threading model [WPF]
- rendering ink [WPF]
- dynamic rendering thread [WPF]
- ink collection plug-in
- plug-ins [WPF], for ink
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
ms.openlocfilehash: 80e7ef202c46a23069766512cf4e67bb21a49564
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007389"
---
# <a name="the-ink-threading-model"></a>インク スレッド モデル
よく似た書き込みと紙とペンの正規表現では、Tablet PC 上のインクの利点の 1 つ。  これを行うには、タブレット ペンは、マウスは、ユーザーの書き込みとして、インクをレンダリングするよりもはるかに高いレートで入力データを収集します。  ブロックになることができますがあるために、アプリケーションのユーザー インターフェイス (UI) スレッドはペン データとレンダリングのインクを収集するために十分ではありません。  これを解決するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが、ユーザーがインクを書き込むときに、追加の 2 つのスレッドを使用します。  
  
 次の一覧には、収集およびデジタル インクの描画に参加しているスレッドがについて説明します。  
  
- ペン スレッドのスレッド、スタイラスからの入力を受け取る。  (実際には、スレッド プールでは、これは、このトピックでは、ペン スレッドとしてそれを参照)。  
  
- アプリケーション ユーザー インターフェイス スレッドで、アプリケーションのユーザー インターフェイスを制御するスレッド。  
  
- 動的レンダリング スレッドで、ユーザーの中に、インクをレンダリングするスレッドは、ストロークを描画します。 Presentation Foundation のウィンドウで説明したように、動的レンダリング スレッドは、アプリケーションの他の UI 要素を描画するスレッドを異なる[スレッド モデル](threading-model.md)します。  
  
 手描き入力のモデルは、同じアプリケーションを使用しているかどうか、<xref:System.Windows.Controls.InkCanvas>またはカスタム コントロールでのような[インク入力コントロールの作成](creating-an-ink-input-control.md)です。  このトピックの観点でスレッド処理について説明しますが、 <xref:System.Windows.Controls.InkCanvas>、カスタム コントロールを作成するときに、同じ概念が適用されます。  
  
## <a name="threading-overview"></a>スレッド処理の概要  
 次の図は、ユーザーがストロークを描画するときに、スレッド処理モデルを示します。  
  
 ![ストローク描画中のスレッド処理モデル。](./media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1. ユーザーがストロークを描画中に発生するアクション  
  
    1. ユーザーがストロークを描画、ときに、ペン スレッド上でスタイラス ポイントが提供されます。  スタイラス プラグインを含む、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ペン スレッド上でスタイラス ポイントをそのまま使用する前にそれらを変更することや、<xref:System.Windows.Controls.InkCanvas>がそれらを受け取る。  
  
    2. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>動的レンダリング スレッド上でスタイラス ポイントを表示します。 これは、前の手順と同時に発生します。  
  
    3. <xref:System.Windows.Controls.InkCanvas> UI スレッド上でスタイラス ポイントを受信します。  
  
2. ユーザーがストロークを終了した後に発生するアクション  
  
    1. ユーザーは、ストロークの描画が完了すると、<xref:System.Windows.Controls.InkCanvas>作成、<xref:System.Windows.Ink.Stroke>オブジェクトし、それに追加、 <xref:System.Windows.Controls.InkPresenter>、静的に表示されます。  
  
    2. UI スレッドのアラート、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>します線が表示される静的にするため、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ストロークのビジュアル表現を削除します。  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>インクの収集とスタイラス プラグイン  
 各<xref:System.Windows.UIElement>が、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>します。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>内のオブジェクト、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>受信し、ペン スレッド上でスタイラス ポイントを変更することができます。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>オブジェクト内の順序に従ってスタイラス ポイントの受信、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>します。  
  
 次の図に、仮定の状況で、<xref:System.Windows.UIElement.StylusPlugIns%2A>のコレクションを<xref:System.Windows.UIElement>が含まれています`stylusPlugin1`、 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、および`stylusPlugin2`点で、順序。  
  
 ![スタイラス プラグインの順序では、出力に影響します。](./media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 前の図で、次の動作が行わをれます。  
  
1. `StylusPlugin1` x の値を変更し、y です。  
  
2. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 変更後のスタイラス ポイントを受信し、動的レンダリング スレッドでレンダリングします。  
  
3. `StylusPlugin2` 変更後のスタイラス ポイントを受信し、さらに x の値を変更し、y です。  
  
4. アプリケーションでは、スタイラス ポイントを収集し、ユーザーがストロークを終了すると、静的にストロークを描画します。  
  
 ものとします`stylusPlugin1`四角形にスタイラス ポイントを制限し、`stylusPlugin2`右側にスタイラス ポイントを変換します。  前のシナリオで、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>受信制限付きのスタイラス ポイントが、翻訳されたスタイラス ポイントではありません。  ユーザーがストロークを描画ストロークは、四角形の境界内レンダリングされますが、ユーザーが、ペンを持ち上げるまでに変換する線が表示されません。  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>操作プラグイン UI スレッド上でスタイラスを実行します。  
 正確なヒット テストは、ペン スレッド上で実行されることはできません、ためにによっては、いくつかの要素がスタイラス入力が他の要素のためのものを受け取ることがあります。 サブスクライブしで操作を実行する操作を実行する前に、入力が正しく回送されたことを確認する必要がある場合、 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>、 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>、または<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A>メソッド。 これらのメソッドは、正確なヒット テストが実行された後に、アプリケーション スレッドによって呼び出されます。 これらのメソッドにサブスクライブする、<xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A>ペン スレッド上で発生するメソッド内のメソッド。  
  
 次の図は、ペン スレッドとのスタイラス イベントに関して UI スレッド間のリレーションシップを<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>します。  
  
 ![インク スレッド モデル&#40;UI およびペン&#41;](./media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>レンダリング インク  
 ユーザーがストロークを描画、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を"flow"ペンから UI スレッドがビジー状態のときにさらに、インクが表示されるように、別のスレッドでインクをレンダリングします。  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>スタイラス ポイントを収集するように、動的レンダリング スレッドで、ビジュアル ツリーを構築します。  ユーザーがストロークを終了すると、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>アプリケーションは次の描画パスと、通知を要求します。  アプリケーションが次の描画パスが完了したら、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>そのビジュアル ツリーをクリーンアップします。  このプロセスを説明する図を次に示します。  
  
 ![インク スレッド ダイアグラム](./media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1. ユーザーがストロークを開始します。  
  
    1. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ビジュアル ツリーを作成します。  
  
2. ユーザーがストロークを描画します。  
  
    1. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ビジュアル ツリーを構築します。  
  
3. ユーザーがストロークを終了します。  
  
    1. <xref:System.Windows.Controls.InkPresenter>ストロークをそのビジュアル ツリーに追加します。  
  
    2. Media Integration Layer (MIL) は、静的にストロークをレンダリングします。  
  
    3. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ビジュアルをクリーンアップします。
