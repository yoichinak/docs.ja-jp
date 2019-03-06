---
title: '方法: ルーティング イベントを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: 42f5f247e775fbf0bd323fc693a74d6149c87bb3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368195"
---
# <a name="how-to-handle-a-routed-event"></a>方法: ルーティング イベントを処理する
バブル イベントの動作と、ルーティング イベント データを処理できるハンドラーを作成する方法を次の例に示します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、要素は、要素ツリー構造体に配置されます。 親要素は、要素ツリー内で最初に子要素が発生させたイベントの処理に参加できます。 これは、イベント ルーティングにより可能です。  
  
 ルーティング イベントは通常、バブルまたはトンネルの 2 つのルーティング方法のいずれかに従います。 この例は、バブル イベントについて説明し、使用、<xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType>ルーティングの動作を表示するイベントです。  
  
 次の例では、2 つ作成されます<xref:System.Windows.Controls.Button>を制御しを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性構文があり、この例では、一般的な親要素にイベント ハンドラーをアタッチする<xref:System.Windows.Controls.StackPanel>します。 それぞれの個々 のイベント ハンドラーをアタッチするのではなく<xref:System.Windows.Controls.Button>子要素では、例では、属性構文を使用してイベント ハンドラーを結び付ける、<xref:System.Windows.Controls.StackPanel>親要素。 このイベント処理パターンは、ハンドラーがアタッチされる要素の数を減らすための手法としてイベント ルーティングを使用する方法を示します。 それぞれのすべてのバブル イベント<xref:System.Windows.Controls.Button>親要素内のルート。  
  
 親に注意して<xref:System.Windows.Controls.StackPanel>要素、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>属性が名前を付けて部分的に修飾されたとして指定したイベントの名前、<xref:System.Windows.Controls.Button>クラス。 <xref:System.Windows.Controls.Button>クラスは、<xref:System.Windows.Controls.Primitives.ButtonBase>派生クラスを持つ、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>そのメンバーの一覧でイベント。 イベント ハンドラーをアタッチするためのこの部分修飾手法が必要になるのは、ルーティング イベント ハンドラーがアタッチされる要素のメンバー一覧に、処理されているイベントが存在しない場合です。  
  
 [!code-xaml[RoutedEventHandle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 次の例のハンドル、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  この例では、イベントを処理する要素とイベントを発生させる要素を報告します。 ユーザーがいずれかのボタンをクリックすると、イベント ハンドラーが実行されます。  
  
 [!code-csharp[RoutedEventHandle#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.RoutedEvent>
- [入力の概要](input-overview.md)
- [ルーティング イベントの概要](routed-events-overview.md)
- [方法トピック](events-how-to-topics.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
