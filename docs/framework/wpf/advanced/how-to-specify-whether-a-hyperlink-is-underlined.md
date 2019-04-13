---
title: '方法: ハイパーリンクに下線を引くかどうかを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 5718912e24a0697f209669b0ab4e7f4df1765ed3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076316"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>方法: ハイパーリンクに下線を引くかどうかを指定する
<xref:System.Windows.Documents.Hyperlink>オブジェクトがインライン レベル フロー コンテンツ要素、フロー コンテンツ内のハイパーリンクをホストすることができます。 既定では、<xref:System.Windows.Documents.Hyperlink>を使用して、<xref:System.Windows.TextDecoration>下線を表示するオブジェクト。 <xref:System.Windows.TextDecoration> 多数ある場合は特に、オブジェクトは処理を要するインスタンスを作成すると、パフォーマンスにできる<xref:System.Windows.Documents.Hyperlink>オブジェクト。 広範に使用する場合<xref:System.Windows.Documents.Hyperlink>要素などのイベントをトリガーするときにのみ下線を表示するのにすることがあります、<xref:System.Windows.ContentElement.MouseEnter>イベント。  
  
 次の例では"My MSN"リンクの下線が動的では、その場合のみ表示されます、<xref:System.Windows.ContentElement.MouseEnter>イベントがトリガーされます。  
  
  ![TextDecorations を表示するハイパーリンク](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)  

## <a name="example"></a>例  
 次のマークアップ サンプルでは、<xref:System.Windows.Documents.Hyperlink>下線なしで定義されています。  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 次のコード サンプルの下線を作成する方法を示しています、<xref:System.Windows.Documents.Hyperlink>上、<xref:System.Windows.ContentElement.MouseEnter>イベント上で削除し、<xref:System.Windows.ContentElement.MouseLeave>イベント。  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [文字の装飾を作成する](how-to-create-a-text-decoration.md)
