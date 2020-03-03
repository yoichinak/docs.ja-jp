---
title: '方法: CompositionTarget を使用したフレームの間隔ごとの描画'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 8864204ccdd1e860cc910dfe8baa2f25edfb2fcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956980"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>方法: CompositionTarget を使用したフレームの間隔ごとの描画
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション エンジンには、フレームベースのアニメーションを作成するためのさまざまな機能が用意されています。 ただし、フレームベースの描画をさらにきめ細かく制御することが必要となるアプリケーション シナリオがあります。 オブジェクト<xref:System.Windows.Media.CompositionTarget>は、フレームごとのコールバックに基づいてカスタムアニメーションを作成する機能を提供します。  
  
 <xref:System.Windows.Media.CompositionTarget>は、アプリケーションが描画される表示サーフェイスを表す静的クラスです。 <xref:System.Windows.Media.CompositionTarget.Rendering>イベントは、アプリケーションのシーンが描画されるたびに発生します。 レンダリング フレーム レートは、1 秒あたりのシーンの描画回数です。  
  
> [!NOTE]
> を使用し<xref:System.Windows.Media.CompositionTarget>た完全なコードサンプルについては、「 [CompositionTarget サンプルの使用](https://go.microsoft.com/fwlink/?LinkID=160045)」を参照してください。  
  
## <a name="example"></a>例  
 イベント<xref:System.Windows.Media.CompositionTarget.Rendering>は、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レンダリングプロセス中に発生します。 次の例は、の<xref:System.EventHandler> <xref:System.Windows.Media.CompositionTarget>静的<xref:System.Windows.Media.CompositionTarget.Rendering>メソッドにデリゲートを登録する方法を示しています。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 独自の描画イベント ハンドラー メソッドを使用して、描画のカスタム コンテンツを作成できます。 このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がビジュアル ツリーの永続化されたレンダリング データを合成シーン グラフにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。 さらに、ビジュアル ツリーに対する変更によって合成シーン グラフが強制的に更新される場合も、イベント ハンドラー メソッドが呼び出されます。 イベント ハンドラー メソッドは、レイアウトが計算された後に呼び出されます。 ただし、イベント ハンドラー メソッド内でレイアウトを変更できます。つまり、そのレイアウトは、描画する前にもう一度計算されることになります。  
  
 次の例は、 <xref:System.Windows.Media.CompositionTarget>イベントハンドラーメソッドにカスタム描画を提供する方法を示しています。 この場合、の背景色<xref:System.Windows.Controls.Canvas>は、マウスの座標位置に基づく色の値を使用して描画されます。 内でマウスを移動すると<xref:System.Windows.Controls.Canvas>、その背景色が変わります。 また、現在の経過時間および描画されたフレームの合計数に基づいて、平均フレーム レートが計算されます。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 カスタム描画は、コンピューターごとに異なる速度で実行される場合があります。 これは、カスタム描画がフレーム レートに依存するためです。 実行しているシステムとそのシステム<xref:System.Windows.Media.CompositionTarget.Rendering>のワークロードによっては、イベントが1秒間に異なる回数だけ呼び出されることがあります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを実行するデバイスのグラフィックス ハードウェアの機能およびパフォーマンスの決定については、「[グラフィックスの描画層](../advanced/graphics-rendering-tiers.md)」を参照してください。  
  
 イベントの発生中に<xref:System.EventHandler>レンダリングデリゲートを追加または削除すると、イベントの発生が終了するまで遅延されます。 これは、基本イベント<xref:System.MulticastDelegate>が共通言語ランタイム (CLR) で処理される方法と一致します。 また、描画イベントが特定の順序で呼び出されるかどうかは保証されません。 特定の順序に<xref:System.EventHandler>依存する複数のデリゲートがある場合は、1つ<xref:System.Windows.Media.CompositionTarget.Rendering>のイベントを登録し、デリゲートを正しい順序で多重化する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.CompositionTarget>
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
