---
title: インクの格納
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
ms.openlocfilehash: aec89286cfac9b0a315dc2d00135543511b2d1ac
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353960"
---
# <a name="storing-ink"></a>インクの格納
<xref:System.Windows.Ink.StrokeCollection.Save%2A>メソッドは、インクとして形式 ISF (Ink Serialized) を格納するためのサポートを提供します。 コンス トラクター、<xref:System.Windows.Ink.StrokeCollection>クラスは、インク データを読み取るためのサポートを提供します。  
  
## <a name="ink-storage-and-retrieval"></a>インクの格納と取得  
 このセクションが格納およびのインクを取得する方法について説明します、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プラットフォーム。  
  
 次の例では、ファイルの保存のダイアログ ボックスをユーザーに提示しからインクを保存するボタンのクリック イベント ハンドラーの実装、<xref:System.Windows.Controls.InkCanvas>ファイルに出力します。  
  
 [!code-csharp[DigitalInkTopics#12](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 次の例では、ファイルを開く ダイアログ ボックスをユーザーに提示し、ファイルからインクを読み取る ボタンのクリック イベント ハンドラーの実装、<xref:System.Windows.Controls.InkCanvas>要素。  
  
 [!code-csharp[DigitalInkTopics#13](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.InkCanvas>
- [Windows Presentation Foundation](../index.md)
