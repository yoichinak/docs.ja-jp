---
title: '方法: アプリケーション ジェスチャを認識する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
ms.openlocfilehash: 99deaa528a089f2d16268747f2e946873f3420a0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370515"
---
# <a name="how-to-recognize-application-gestures"></a>方法: アプリケーション ジェスチャを認識する
次の例では、ユーザーとインクを消去する方法、<xref:System.Windows.Ink.ApplicationGesture.ScratchOut>でジェスチャを<xref:System.Windows.Controls.InkCanvas>します。 この例では、<xref:System.Windows.Controls.InkCanvas>という`inkCanvas1`、XAML ファイルで宣言されます。  
  
## <a name="example"></a>例  
 [!code-csharp[HowToRecognizeGestures#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Ink.ApplicationGesture>
- <xref:System.Windows.Controls.InkCanvas>
- <xref:System.Windows.Controls.InkCanvas.Gesture>
