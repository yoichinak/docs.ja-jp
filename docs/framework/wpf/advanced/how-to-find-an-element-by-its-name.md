---
title: '方法: 要素を名前で検索する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
ms.openlocfilehash: 7405f9ba8db5d4db0ce35ca250f13e456685f39b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351049"
---
# <a name="how-to-find-an-element-by-its-name"></a>方法: 要素を名前で検索する
この例は、使用する方法を説明します、<xref:System.Windows.FrameworkElement.FindName%2A>要素を検索する方法、<xref:System.Windows.FrameworkElement.Name%2A>値。  
  
## <a name="example"></a>例  
 この例では、その名前で特定の要素を検索するメソッドはボタンのイベント ハンドラーとして書き込まれます。 `stackPanel` <xref:System.Windows.FrameworkElement.Name%2A>ルートの<xref:System.Windows.FrameworkElement>検索対象を示し、メソッドの例、視覚的に、検出された要素としてキャストすることによって<xref:System.Windows.Controls.TextBlock>のいずれかを変更して、<xref:System.Windows.Controls.TextBlock>表示[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]プロパティ。  
  
 [!code-csharp[FEFindName#Find](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
