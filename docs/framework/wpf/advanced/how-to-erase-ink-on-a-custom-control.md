---
title: '方法: カスタム コントロールでインクを消去する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
ms.openlocfilehash: 60e2af64cb0c5b313f4f1201cab70da6a88f61e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365894"
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>方法: カスタム コントロールでインクを消去する
<xref:System.Windows.Ink.IncrementalStrokeHitTester>現在描画ストロークに別のストロークと交差しているかどうかを決定します。  ストロークの一部を消去するユーザーをできるようにするコントロールを作成するのに便利ですが、方法、ユーザーが、<xref:System.Windows.Controls.InkCanvas>ときに、<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>に設定されている<xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>します。  
  
## <a name="example"></a>例  
 次の例では、ユーザーがストロークの一部を消去できるようにするカスタム コントロールを作成します。  この例では、初期化時に、インクを格納しているコントロールを作成します。  インクを収集するコントロールを作成するを参照してください。[インク入力コントロールの作成](creating-an-ink-input-control.md)です。  
  
 [!code-csharp[HowToEraseInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
