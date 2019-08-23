---
title: '方法: コードを使用してイベント ハンドラーを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 017b32dc07f62cc4553a84f7b91687fb34a53c65
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937472"
---
# <a name="how-to-add-an-event-handler-using-code"></a>方法: コードを使用してイベント ハンドラーを追加する
この例では、コードを使用して、イベントハンドラーを要素に追加する方法を示します。  
  
 イベントハンドラーを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素に追加する場合、その要素を含むマークアップページが既に読み込まれている場合は、コードを使用してハンドラーを追加する必要があります。 また、コードを使用してアプリケーションの要素ツリーを完全に構築し、を使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素を宣言していない場合は、特定のメソッドを呼び出して、構築された要素ツリーにイベントハンドラーを追加できます。  
  
## <a name="example"></a>例  
 次の例では、 <xref:System.Windows.Controls.Button>最初にで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義された既存のページに新しいを追加します。 分離コードファイルは、イベントハンドラーメソッドを実装し、そのメソッドをの<xref:System.Windows.Controls.Button>新しいイベントハンドラーとして追加します。  
  
 このC#例では`+=` 、演算子を使用してハンドラーをイベントに割り当てています。 これは、共通言語ランタイム (CLR) イベント処理モデルでハンドラーを割り当てるために使用される演算子と同じです。 Microsoft Visual Basic では、イベントハンドラーを追加する手段として、この演算子はサポートされていません。 代わりに、次の2つの方法のいずれかが必要です。  
  
- イベントハンドラーの実装を参照する`AddressOf`には、メソッドを演算子と共に使用します。<xref:System.Windows.UIElement.AddHandler%2A>  
  
- イベントハンドラー `Handles`定義の一部としてキーワードを使用します。 この手法は、ここでは示していません。「 [Visual Basic と WPF のイベント処理」を](visual-basic-and-wpf-event-handling.md)参照してください。  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> 最初に解析[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]されたページにイベントハンドラーを追加する方がはるかに簡単です。 イベントハンドラーを追加するオブジェクト要素内で、処理するイベントの名前と一致する属性を追加します。 次に、その属性の値を、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページの分離コードファイルで定義したイベントハンドラーメソッドの名前として指定します。 詳細については、「 [XAML の概要 (WPF)](xaml-overview-wpf.md) 」または「[ルーティングイベントの概要](routed-events-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ルーティング イベントの概要](routed-events-overview.md)
- [方法トピック](events-how-to-topics.md)
