---
title: '方法: 要素およびコントロールのマージンを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
ms.openlocfilehash: 3263810806b6b4bbec15eadfd1f1da3a57d12698
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356274"
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>方法: 要素およびコントロールのマージンを設定する
この例の説明を設定する方法、<xref:System.Windows.FrameworkElement.Margin%2A>分離コードで余白の幅を既存のプロパティ値を変更することで、プロパティ。 <xref:System.Windows.FrameworkElement.Margin%2A>プロパティのプロパティである、<xref:System.Windows.FrameworkElement>要素の基本し、さまざまなコントロールとその他の要素によって継承されるためです。  
  
 この例で記述された[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、分離コード ファイルを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を参照します。 両方の分離コードが示すように、C#と Microsoft Visual Basic バージョン。  
  
## <a name="example"></a>例  
 [!code-xaml[FEMarginProgrammatic#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
