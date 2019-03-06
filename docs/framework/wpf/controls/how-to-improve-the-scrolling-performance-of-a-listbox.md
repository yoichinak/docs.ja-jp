---
title: '方法: ListBox のスクロール速度を向上させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: a9d1ca1d8ac2ef830984408f3052eb0ed0987c5d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364555"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>方法: ListBox のスクロール速度を向上させる
場合、<xref:System.Windows.Controls.ListBox>多くの項目を格納、ユーザーがスクロールすると、ユーザー インターフェイスの応答が遅くなること、<xref:System.Windows.Controls.ListBox>をマウス ホイールを使用するかスクロール バーのつまみをドラッグします。 パフォーマンスを向上させることができます、<xref:System.Windows.Controls.ListBox>を設定してユーザーがスクロールすると、`VirtualizingStackPanel.VirtualizationMode`添付プロパティを<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>します。  
  
## <a name="example"></a>例  
  
## <a name="description"></a>説明  
次の例では、作成、<xref:System.Windows.Controls.ListBox>設定と、`VirtualizingStackPanel.VirtualizationMode`添付プロパティを<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>スクロール中にパフォーマンスを向上させる。  
  
## <a name="code"></a>コード  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 次の例では、前の例を使用してデータを示します。  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
