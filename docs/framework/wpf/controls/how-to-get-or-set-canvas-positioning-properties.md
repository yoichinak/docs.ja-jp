---
title: '方法: Canvas の配置プロパティを取得または設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 9b280bf86f12b406582cb2f534edb85618515d76
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356326"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a>方法: Canvas の配置プロパティを取得または設定する
この例の配置のメソッドを使用する方法を示しています、<xref:System.Windows.Controls.Canvas>要素は子コンテンツを配置します。 この例でコンテンツを使用して、<xref:System.Windows.Controls.ListBoxItem>を表す位置の値し、のインスタンスに値を変換します。 <xref:System.Double>、配置に必要な引数であります。 値が文字列に変換し、テキストとして表示、<xref:System.Windows.Controls.TextBlock>要素を使用して、<xref:System.Windows.Controls.Canvas.GetLeft%2A>メソッド。  
  
## <a name="example"></a>例  
 次の例では、作成、<xref:System.Windows.Controls.ListBox>選択可能な 11 個の要素<xref:System.Windows.Controls.ListBoxItem>要素。 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>イベント トリガー、`ChangeLeft`カスタム メソッドは、後続のコード ブロックを定義します。  
  
 各<xref:System.Windows.Controls.ListBoxItem>を表す、<xref:System.Double>引数の 1 つの値を<xref:System.Windows.Controls.Canvas.SetLeft%2A>メソッドの<xref:System.Windows.Controls.Canvas>受け入れます。 使用するには、<xref:System.Windows.Controls.ListBoxItem>のインスタンスを表す<xref:System.Double>、最初に変換する必要があります、<xref:System.Windows.Controls.ListBoxItem>正しいデータ型にします。  
  
 [!code-xaml[CanvasPositioningProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 ユーザーが変更されたとき、<xref:System.Windows.Controls.ListBox>選択した場合、起動、`ChangeLeft`カスタム メソッド。 このメソッドは、<xref:System.Windows.Controls.ListBoxItem>を<xref:System.Windows.LengthConverter>に変換するオブジェクト、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Double>(この値は既にに変換されたに注意してください、<xref:System.String>を使用して、 <xref:System.Windows.Controls.Control.ToString%2A>メソッドの場合)。 この値が渡されたし、<xref:System.Windows.Controls.Canvas.SetLeft%2A>と<xref:System.Windows.Controls.Canvas.GetLeft%2A>メソッドの<xref:System.Windows.Controls.Canvas>の位置を変更するには、`text1`オブジェクト。  
  
 [!code-csharp[CanvasPositioningProperties#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.ListBoxItem>
- <xref:System.Windows.LengthConverter>
- [パネルの概要](panels-overview.md)
