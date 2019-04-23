---
title: '方法: ICommandSource を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 218a17f221598ac29213bd28a0f04adb16bc933b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107368"
---
# <a name="how-to-implement-icommandsource"></a>方法: ICommandSource を実装する
この例は、実装することで、コマンド ソースを作成する方法を示しています。<xref:System.Windows.Input.ICommandSource>します。  コマンド ソースは、コマンドを呼び出す方法を認識しているオブジェクトです。  <xref:System.Windows.Input.ICommandSource>インターフェイスで公開される 3 つのメンバー: <xref:System.Windows.Input.ICommandSource.Command%2A>、 <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>、および<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>します。  <xref:System.Windows.Input.ICommandSource.Command%2A> 呼び出されるコマンドです。 <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>がコマンド ソースからコマンドを処理するメソッドに渡されるユーザー定義データ型。 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>でコマンドが実行されているオブジェクトです。  
  
 この例で、クラスのサブクラスが作成、<xref:System.Windows.Controls.Slider>コントロールと実装<xref:System.Windows.Input.ICommandSource>します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 実装するクラスのいくつか提供されます<xref:System.Windows.Input.ICommandSource>など<xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.MenuItem>、および<xref:System.Windows.Controls.ListBoxItem>します。  コマンド ソースは、コマンドを呼び出す方法を定義します。   <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.MenuItem>クリックしてされたときに、コマンドを呼び出します。  A<xref:System.Windows.Controls.ListBoxItem>ダブルクリックされたときにコマンドを呼び出します。 これらのクラスでは、コマンドのみになるソース、<xref:System.Windows.Input.ICommandSource.Command%2A>プロパティを設定します。  
  
 この例では、スライダーを移動すると、コマンドを呼び出すより正確には、ときに、<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>プロパティを変更します。  
  
 クラス定義は、次のとおりです。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 次の手順を実装するためには、<xref:System.Windows.Input.ICommandSource>メンバー。  この例では、プロパティとして実装されます<xref:System.Windows.DependencyProperty>オブジェクト。  これにより、データ バインディングを使用するプロパティです。  詳細については、<xref:System.Windows.DependencyProperty>クラスを参照してください、[依存関係プロパティの概要](dependency-properties-overview.md)します。  データ バインディングの詳細については、次を参照してください。、[データ バインディングの概要](../data/data-binding-overview.md)します。  
  
 のみ、<xref:System.Windows.Input.ICommandSource.Command%2A>プロパティが次に示します。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 次に、<xref:System.Windows.DependencyProperty>コールバックを変更します。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 次の手順を追加およびコマンド ソースに関連付けられているコマンドを削除します。  <xref:System.Windows.Input.ICommandSource.Command%2A>プロパティだけために上書きできません新しいコマンドが追加されたときにイベント ハンドラーは、前のコマンドに関連付けられている場合は 1 つを最初に削除する必要があります。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 最後に、ロジックを作成、<xref:System.Windows.Input.ICommand.CanExecuteChanged>ハンドラーと<xref:System.Windows.Input.ICommand.Execute%2A>メソッド。  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged>イベントは、現在のコマンド ターゲットで実行するコマンドの機能が変更された可能性がありますがコマンド ソースを通知します。  通常呼び出しコマンド ソースは、このイベントを受け取ると、<xref:System.Windows.Input.ICommand.CanExecute%2A>コマンドのメソッド。  現在のコマンド ターゲットでコマンドを実行できない場合、通常は、コマンド ソースが無効にします。  現在のコマンド ターゲットでコマンドを実行できるの場合、通常は、コマンド ソースが有効にします。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 最後の手順は、<xref:System.Windows.Input.ICommand.Execute%2A>メソッド。  コマンドの場合、 <xref:System.Windows.Input.RoutedCommand>、 <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A>メソッドが呼び出される。 それ以外の<xref:System.Windows.Input.ICommand><xref:System.Windows.Input.ICommand.Execute%2A>メソッドが呼び出されます。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [コマンド実行の概要](commanding-overview.md)
