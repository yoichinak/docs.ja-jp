---
title: '方法: GridLengthConverter オブジェクトを作成および使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: 0455d91eff820e5c087af20207ece1313f6f3a39
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352257"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>方法: GridLengthConverter オブジェクトを作成および使用する
## <a name="example"></a>例  
 次の例は、作成しのインスタンスを使用する方法を示しています。<xref:System.Windows.GridLengthConverter>します。 例では、呼び出されるカスタム メソッドを定義します。 `changeCol`、どのパス、<xref:System.Windows.Controls.ListBoxItem>を、<xref:System.Windows.GridLengthConverter>に変換する、<xref:System.Windows.Controls.ContentControl.Content%2A>の、<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Windows.GridLength>。 変換後の値がの値として戻されますが、<xref:System.Windows.Controls.ColumnDefinition.Width%2A>のプロパティ、<xref:System.Windows.Controls.ColumnDefinition>要素。  
  
 この例では、という 2 つ目のカスタム メソッドも定義します`changeColVal`します。 このカスタム メソッドに変換、<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>の<xref:System.Windows.Controls.Slider>を<xref:System.String>と値のバックアップに移ります、<xref:System.Windows.Controls.ColumnDefinition>として、<xref:System.Windows.Controls.ColumnDefinition.Width%2A>要素の。  
  
 なお、個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルの内容を定義する、 <xref:System.Windows.Controls.ListBoxItem>。  
  
 [!code-csharp[gridlengthConverterGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
