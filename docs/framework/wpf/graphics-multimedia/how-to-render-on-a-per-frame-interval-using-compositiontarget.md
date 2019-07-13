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
ms.openlocfilehash: 00b416d423a4bdc8bab576add2d77fd305ea6e0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008929"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>方法: CompositionTarget を使用したフレームの間隔ごとの描画
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション エンジンには、フレームベースのアニメーションを作成するためのさまざまな機能が用意されています。 ただし、フレームベースの描画をさらにきめ細かく制御することが必要となるアプリケーション シナリオがあります。 <xref:System.Windows.Media.CompositionTarget>オブジェクトは、フレームごとのコールバックに基づいてカスタム アニメーションを作成する機能を提供します。  
  
 <xref:System.Windows.Media.CompositionTarget> アプリケーションが描画される表示サーフェイスを表す静的クラスです。 <xref:System.Windows.Media.CompositionTarget.Rendering>イベントは、アプリケーションのシーンが描画されるたびに発生します。 レンダリング フレーム レートは、1 秒あたりのシーンの描画回数です。  
  
> [!NOTE]
>  使用して完全なコード サンプルの<xref:System.Windows.Media.CompositionTarget>を参照してください[CompositionTarget のサンプルを使用して](https://go.microsoft.com/fwlink/?LinkID=160045)します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.CompositionTarget.Rendering>中にイベントが発生した、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レンダリング プロセス。 次の例は、登録する方法を示しています。、 <xref:System.EventHandler> 、静的な委任<xref:System.Windows.Media.CompositionTarget.Rendering>メソッド<xref:System.Windows.Media.CompositionTarget>します。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 独自の描画イベント ハンドラー メソッドを使用して、描画のカスタム コンテンツを作成できます。 このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がビジュアル ツリーの永続化されたレンダリング データを合成シーン グラフにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。 さらに、ビジュアル ツリーに対する変更によって合成シーン グラフが強制的に更新される場合も、イベント ハンドラー メソッドが呼び出されます。 イベント ハンドラー メソッドは、レイアウトが計算された後に呼び出されます。 ただし、イベント ハンドラー メソッド内でレイアウトを変更できます。つまり、そのレイアウトは、描画する前にもう一度計算されることになります。  
  
 次の例は指定したカスタムの描画、<xref:System.Windows.Media.CompositionTarget>イベント ハンドラー メソッド。 ここでの背景色、<xref:System.Windows.Controls.Canvas>の描画にマウスの座標位置に基づく色の値を使用します。 内でマウスを移動する場合、 <xref:System.Windows.Controls.Canvas>、その背景の色を変更します。 また、現在の経過時間および描画されたフレームの合計数に基づいて、平均フレーム レートが計算されます。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 カスタム描画は、コンピューターごとに異なる速度で実行される場合があります。 これは、カスタム描画がフレーム レートに依存するためです。 実行しているシステムと、そのシステムのワークロードに応じて、<xref:System.Windows.Media.CompositionTarget.Rendering>異なる回数 1 秒あたりのイベントを呼び出すことができます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを実行するデバイスのグラフィックス ハードウェアの機能およびパフォーマンスの決定については、「[グラフィックスの描画層](../advanced/graphics-rendering-tiers.md)」を参照してください。  
  
 追加または削除を表示する<xref:System.EventHandler>デリゲート、イベントの発生中には、イベントの終了後まで遅延されますを起動します。 これは、一貫性のある方法で<xref:System.MulticastDelegate>-ベースのイベントは共通言語ランタイム (CLR) で処理されます。 また、描画イベントが特定の順序で呼び出されるかどうかは保証されません。 複数ある場合<xref:System.EventHandler>特定の順序に依存するデリゲート、1 つを登録する必要があります<xref:System.Windows.Media.CompositionTarget.Rendering>イベントとマルチプレクシングが適切でデリゲートでは、自分で注文します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.CompositionTarget>
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
