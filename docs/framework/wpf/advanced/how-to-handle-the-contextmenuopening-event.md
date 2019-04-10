---
title: '方法: ContextMenuOpening イベントを処理する'
ms.date: 03/30/2017
helpviewer_keywords:
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
ms.openlocfilehash: 65a1e34d5b078c49bf59c2d9787812940c9a7494
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340400"
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>方法: ContextMenuOpening イベントを処理する
<xref:System.Windows.FrameworkElement.ContextMenuOpening>か、既存のコンテキスト メニューの前を表示するかを設定して表示されるメニューを抑制するを調整するアプリケーションでイベントを処理すること、<xref:System.Windows.RoutedEventArgs.Handled%2A>プロパティを`true`イベント データ。 設定の一般的な理由<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`メニューを置き換えるだけで、新しいデータのイベントは<xref:System.Windows.Controls.ContextMenu>オブジェクト、操作を取り消すと、新しいオープンを開始することもあります必要があります。 ハンドラーを記述する場合、<xref:System.Windows.FrameworkElement.ContextMenuOpening>イベント、注意すべきタイミングの問題との間の<xref:System.Windows.Controls.ContextMenu>コントロールとサービスを開くと、コントロールのコンテキスト メニューを通常配置を担当します。 このトピックでは、コンテキスト メニューのさまざまなシナリオを開くコードの手法の一部を示していて、タイミングの問題が関係する状況を示しています。  
  
 処理のためのいくつかのシナリオ、<xref:System.Windows.FrameworkElement.ContextMenuOpening>イベント。  
  
-   表示する前に、メニュー項目を調整します。  
  
-   表示する前にメニュー全体を置き換えます。  
  
-   完全に任意の既存のコンテキスト メニューを抑制して、コンテキスト メニューを表示していません。  
  
## <a name="example"></a>例  
  
## <a name="adjusting-the-menu-items-before-display"></a>表示する前に、メニュー項目を調整します。  
 既存のメニュー項目を調整することは非常に単純と、最も一般的なシナリオでは可能性があります。 追加するか、アプリケーションの現在の状態情報またはコンテキスト メニューが要求されているオブジェクトのプロパティとして使用できる特定の状態情報への応答のコンテキスト メニュー オプションを減算するためにこれを行う場合があります。  
  
 一般的な技法は、ある特定のコントロールを右クリックすると、イベントのソースを取得し、<xref:System.Windows.FrameworkElement.ContextMenu%2A>からプロパティ。 チェックする通常、<xref:System.Windows.Controls.ItemsControl.Items%2A>既にメニューで、存在し、追加し、削除適切な新しいコンテキスト メニュー項目を表示するコレクション<xref:System.Windows.Controls.MenuItem>にまたはコレクションから項目。  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>表示する前にメニュー全体を置き換える  
 別のシナリオでは、全体のコンテキスト メニューを置換するかどうかです。 既存のコンテキスト メニューのすべての項目を削除し、項目の 0 から始まる新しいものを追加する上記のコードのバリエーションも使用してもちろんでした。 コンテキスト メニューのすべての項目を置換するためより直感的なアプローチが新たに作成するには<xref:System.Windows.Controls.ContextMenu>、項目では、そこに設定して、<xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>に新しいコントロールのプロパティの<xref:System.Windows.Controls.ContextMenu>します。  
  
 置換するための単純なハンドラー コードを次に、<xref:System.Windows.Controls.ContextMenu>します。 このコードでカスタム参照`BuildMenu`メソッドが呼び出されるためによって分離例ハンドラーの 1 つ以上。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 ただし、このスタイルのハンドラーを使用する場合<xref:System.Windows.FrameworkElement.ContextMenuOpening>場合、可能性のあるタイミングの問題を公開することができます、オブジェクトを設定している、<xref:System.Windows.Controls.ContextMenu>既存のコンテキスト メニューはありません。 ユーザーがコントロールを右クリックしたとき<xref:System.Windows.FrameworkElement.ContextMenuOpening>が発生した場合でも、既存<xref:System.Windows.Controls.ContextMenu>が空または null。 ここでは、任意の新しい<xref:System.Windows.Controls.ContextMenu>ソースを設定して表示する要素が遅すぎますが到着します。 また、ユーザーをもう一度を右クリックする場合に、今回は、新しい<xref:System.Windows.Controls.ContextMenu>が表示されたら、値が null 以外と、ハンドラーが正しく置換ハンドラーを 2 回目の実行時にメニューを表示します。 これは、2 つの方法を示しています。  
  
1. できることが保証<xref:System.Windows.FrameworkElement.ContextMenuOpening>常に、少なくともプレース ホルダーを持つコントロールに対して実行ハンドラー <xref:System.Windows.Controls.ContextMenu> 、使用可能なハンドラー コードによって置き換えられる対象。 この場合は、前の例に示すようにハンドラーを使用することもできますが、通常のプレース ホルダーを指定する<xref:System.Windows.Controls.ContextMenu>初期のマークアップで。  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2. ある初期<xref:System.Windows.Controls.ContextMenu>値が null で、いくつかの暫定版のロジックに基づいて。 いずれかのチェックをでした<xref:System.Windows.Controls.ContextMenu>を少なくとも 1 回の null の場合、またはハンドラーがされているかどうかをチェックするコードのフラグを使用して実行します。 想定していますので、<xref:System.Windows.Controls.ContextMenu>に表示される、ハンドラーの詳細については、設定<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`イベント データ。 <xref:System.Windows.Controls.ContextMenuService>コンテキスト メニューの表示を担当するが、`true`値<xref:System.Windows.RoutedEventArgs.Handled%2A>イベントのデータが、コンテキスト メニューの表示を取り消す/イベントを発生させたの組み合わせを制御する要求を表します。  
  
 次の手順は、新しくを指定するは、可能性のある問題のあるコンテキスト メニューは表示されませんが、これで、それを表示します。 以前のハンドラーと同じ 1 つは基本的に新しい設定: 新しいをビルドする<xref:System.Windows.Controls.ContextMenu>コントロールのソースの設定と<xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>プロパティにします。 追加の手順は、最初の試行を抑制するため、コンテキスト メニューの表示を今すぐ強制する必要があります。 表示を強制的に設定する、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType>プロパティを`true`ハンドラー内で。 注意、これを行うときに発生、ハンドラーで、コンテキスト メニューを開くため、<xref:System.Windows.FrameworkElement.ContextMenuOpening>もう一度イベント。 ハンドラーを再入力する再帰を無限になります。 これは、常に確認する必要がある理由`null`または内からコンテキスト メニューを開く場合にフラグを使用して、<xref:System.Windows.FrameworkElement.ContextMenuOpening>イベント ハンドラー。  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>既存のどのコンテキスト メニューを抑制して、コンテキスト メニューを表示していません  
 最後のシナリオでは、完全には、メニューを抑制するハンドラーの記述は一般的ではありません。 場合は、特定のコントロールは、コンテキスト メニューを表示することはできません、ユーザーが要求するときに、メニューを抑制することでこのことを保証するために方が適切な方法があります。 コンテキスト メニューを抑制して、何も表示するハンドラーを使用する場合、ハンドラーを設定するだけですが、<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`イベント データ。 <xref:System.Windows.Controls.ContextMenuService>を担当コンテキスト メニューを表示するは、コントロールが発生したイベントのイベント データを確認します。 イベントが設定されていた場合<xref:System.Windows.RoutedEventArgs.Handled%2A>任意の場所、経路上、イベントが発生したコンテキスト メニュー オープン操作は抑制されます。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>
- [基本要素の概要](base-elements-overview.md)
- [ContextMenu の概要](../controls/contextmenu-overview.md)
