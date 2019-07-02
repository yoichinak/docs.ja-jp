---
title: アルファ ブレンドの直線と塗りつぶし
ms.date: 03/30/2017
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
ms.openlocfilehash: 66061341ee6539e2172c537a0b2a6ec9ff87565c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506113"
---
# <a name="alpha-blending-lines-and-fills"></a>アルファ ブレンドの直線と塗りつぶし
GDI + では、色は、アルファ、赤、緑、および青の 8 ビットごとの 32 ビット値です。 アルファ値を色の透明度を示します: 範囲を色が背景色とブレンドされます。 アルファ値の範囲は 0 ~ 255、0 が完全に透明色を表します、255 は、完全に不透明な色を表します。  
  
 アルファ ブレンドは、ソースとバック グラウンドのカラー データのピクセルを描画します。 指定したソースの色の 3 つのコンポーネント (赤、緑、青) は、次の数式に従って背景色の対応する要素とブレンドされます。  
  
 displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255  
  
 たとえば、元の色の赤の要素は 150、背景色の赤のコンポーネントは 100 です。 アルファ値が 200 の場合は、結果の色の赤の要素がように計算されます。  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 不透明な直線および半透明な直線を描画します。](how-to-draw-opaque-and-semitransparent-lines.md)  
 アルファ ブレンドの直線を描画する方法を示します。  
  
 [方法: 不透明な直線および半透明ブラシを使用して描画します。](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 アルファ ブレンド ブラシを使用する方法について説明します。  
  
 [方法: アルファ ブレンドを制御する複合モードを使用して、](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 使用してアルファ ブレンドを制御する方法について説明します<xref:System.Drawing.Drawing2D.CompositingMode>します。  
  
 [方法: カラー行列を使用して、イメージのアルファ値を設定するには](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 使用する方法について説明します、<xref:System.Drawing.Imaging.ColorMatrix>アルファ ブレンドを制御するオブジェクト。
