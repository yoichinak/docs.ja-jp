---
title: '方法: コマンドを有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
ms.openlocfilehash: a24a7a31154de58051677ba41496fcf4da3f2568
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355065"
---
# <a name="how-to-enable-a-command"></a>方法: コマンドを有効にする
次の例でコマンド処理を使用する方法を示します[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。  関連付ける方法の例を<xref:System.Windows.Input.RoutedCommand>を<xref:System.Windows.Controls.Button>、作成、<xref:System.Windows.Input.CommandBinding>を実装するイベント ハンドラーを作成し、 <xref:System.Windows.Input.RoutedCommand>。  コマンド実行の詳細については、、[コマンド実行の概要](commanding-overview.md)を参照してください。  
  
## <a name="example"></a>例  
 コードの最初のセクションを作成、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]から構成される、<xref:System.Windows.Controls.Button>と<xref:System.Windows.Controls.StackPanel>、し、作成、<xref:System.Windows.Input.CommandBinding>とコマンド ハンドラーに関連付ける、 <xref:System.Windows.Input.RoutedCommand>。  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A>のプロパティ、<xref:System.Windows.Controls.Button>に関連付けられている、<xref:System.Windows.Input.ApplicationCommands.Close%2A>コマンド。  
  
 <xref:System.Windows.Input.CommandBinding>に追加されます、<xref:System.Windows.Input.CommandBindingCollection>ルートの<xref:System.Windows.Window>します。 <xref:System.Windows.Input.CommandBinding.Executed>と<xref:System.Windows.Input.CommandBinding.CanExecute>イベント ハンドラーがこのバインディングにアタッチされているしに関連付けられている、<xref:System.Windows.Input.ApplicationCommands.Close%2A>コマンド。  
  
 なし、<xref:System.Windows.Input.CommandBinding>コマンド ロジック、のみコマンドを実行するためのメカニズムはありません。  ときに、<xref:System.Windows.Controls.Button>がクリックされた、 <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent>後に、コマンド ターゲットで発生しますが、 <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>します。  これらのイベントを探して、要素ツリーの走査、<xref:System.Windows.Input.CommandBinding>の特定のコマンド。  を注目に値します<xref:System.Windows.RoutedEvent>トンネルとバブル要素ツリーを通じて、注意が必要で、<xref:System.Windows.Input.CommandBinding>配置されます。   場合、<xref:System.Windows.Input.CommandBinding>コマンド ターゲットまたはのルートではないに別のノードの兄弟では、 <xref:System.Windows.RoutedEvent>、<xref:System.Windows.Input.CommandBinding>アクセスできません。  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 コードの実装の次のセクション、<xref:System.Windows.Input.CommandManager.Executed>と<xref:System.Windows.Input.CommandBinding.CanExecute>イベント ハンドラー。  
  
 <xref:System.Windows.Input.CommandManager.Executed>ハンドラーが呼び出すメソッドを開いているファイルを閉じます。  <xref:System.Windows.Input.CommandBinding.CanExecute>ハンドラーは、ファイルが開いているかどうかを判断するメソッドを呼び出します。  ファイルが開いて場合<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>に設定されている`true`。 それ以外に設定されている`false`します。  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>関連項目
- [コマンド実行の概要](commanding-overview.md)
