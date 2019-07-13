---
title: '方法: MatrixTransform を使用してカスタム変換を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: aeccb961db539d4cc6dea75fb487fba06e59d6de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769266"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>方法: MatrixTransform を使用してカスタム変換を作成する
この例は、使用する方法を示します、<xref:System.Windows.Media.MatrixTransform>変換 (移動) する位置を stretch との差を<xref:System.Windows.Controls.Button>します。  
  
> [!NOTE]
>  使用、<xref:System.Windows.Media.MatrixTransform>によって提供されないカスタム変換を作成するクラス、 <xref:System.Windows.Media.RotateTransform>、 <xref:System.Windows.Media.SkewTransform>、 <xref:System.Windows.Media.ScaleTransform>、または<xref:System.Windows.Media.TranslateTransform>のクラス。  
  
## <a name="example"></a>例  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [変換の概要](transforms-overview.md)
- [方法トピック](transformations-how-to-topics.md)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
