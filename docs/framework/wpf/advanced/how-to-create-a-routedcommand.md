---
title: '方法: RoutedCommand を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: d433658a3039c262d2f682eff09df646d978018c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109045"
---
# <a name="how-to-create-a-routedcommand"></a>方法: RoutedCommand を作成する
カスタムを作成する方法を示します<xref:System.Windows.Input.RoutedCommand>を作成して、カスタム コマンドを実装する方法と、<xref:System.Windows.Input.ExecutedRoutedEventHandler>と<xref:System.Windows.Input.CanExecuteRoutedEventHandler>にアタッチし、<xref:System.Windows.Input.CommandBinding>します。  コマンド実行の詳細については、次を参照してください。、[コマンド実行の概要](commanding-overview.md)します。  
  
## <a name="example"></a>例  
 最初の手順で作成、<xref:System.Windows.Input.RoutedCommand>コマンドを定義して、インスタンス化することができます。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 アプリケーションで、コマンドを使用するには、コマンドの内容を定義するイベント ハンドラーを作成する必要があります。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 次に、<xref:System.Windows.Input.CommandBinding>作成コマンドにイベント ハンドラーを関連付けます。 <xref:System.Windows.Input.CommandBinding>特定のオブジェクトが作成されます。  このオブジェクトのスコープを定義する、<xref:System.Windows.Input.CommandBinding>要素ツリー  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 最後の手順では、コマンドを呼び出すことです。  コマンドを呼び出す方法の 1 つは、それを関連付ける、<xref:System.Windows.Input.ICommandSource>など、<xref:System.Windows.Controls.Button>します。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 ボタンがクリックされたときに、 <xref:System.Windows.Input.RoutedCommand.Execute%2A> 、カスタム<xref:System.Windows.Input.RoutedCommand>が呼び出されます。  <xref:System.Windows.Input.RoutedCommand>発生させる、<xref:System.Windows.Input.CommandManager.PreviewExecuted>と<xref:System.Windows.Input.CommandManager.Executed>ルーティング イベント。  これらのイベントを探して、要素ツリーの走査、<xref:System.Windows.Input.CommandBinding>この特定のコマンド。  場合、<xref:System.Windows.Input.CommandBinding>が見つかると、<xref:System.Windows.Input.ExecutedRoutedEventHandler>に関連付けられている<xref:System.Windows.Input.CommandBinding>が呼び出されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Input.RoutedCommand>
- [コマンド実行の概要](commanding-overview.md)
