---
title: '方法 : Viewport3D でヒット テストを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D visuals [WPF], hit-testing for
- hit tests [WPF], for 3D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 34bc86349332293e40aca5743cbabb2a48634da6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112090"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a>方法 : Viewport3D でヒット テストを実行する

この例では、 で 3D ビジュアルのヒット<xref:System.Windows.Controls.Viewport3D>テストを実行する方法を示します。

2D および 3D 情報を返すため<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>、テスト結果を反復処理して 3D 結果のみを読み取ることができます。

[!code-csharp[HitTest3D#HitTest3D3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
[!code-vb[HitTest3D#HitTest3D3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]

次<xref:System.Windows.Media.HitTestResultBehavior>のコードでは、ヒット テストの結果の処理方法を決定します。 `UpdateResultInfo`ローカル`UpdateMaterial`で定義されたメソッドです。

[!code-csharp[HitTest3D#HitTest3D3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
[!code-vb[HitTest3D#HitTest3D3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]
