---
title: '方法 : ICommandSource を実装する'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6c18e0b77ec53d9bd3e7ce610f2940effe603c88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174694"
---
# <a name="how-to-implement-icommandsource"></a>方法 : ICommandSource を実装する

この例では、 を実装<xref:System.Windows.Input.ICommandSource>してコマンド ソースを作成する方法を示します。 コマンド ソースは、コマンドを呼び出す方法を知っているオブジェクトです。 この<xref:System.Windows.Input.ICommandSource>インターフェイスは、次の 3 つのメンバーを公開します。

- <xref:System.Windows.Input.ICommandSource.Command%2A>: 呼び出されるコマンド。
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: コマンド ソースからコマンドを処理するメソッドに渡されるユーザー定義データ型。
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: コマンドが実行されるオブジェクト。

この例では、<xref:System.Windows.Controls.Slider>コントロールから継承し、インターフェイスを実装するクラスを作成します。 <xref:System.Windows.Input.ICommandSource>
  
## <a name="example"></a>例

<xref:System.Windows.Input.ICommandSource>WPF には、 <xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.MenuItem>、、および を実装する<xref:System.Windows.Documents.Hyperlink>クラスが多数用意されています。 コマンド ソースは、コマンドを呼び出す方法を定義します。 これらのクラスは、クリックされたときにコマンドを呼び出し、<xref:System.Windows.Input.ICommandSource.Command%2A>プロパティが設定されている場合にのみコマンド ソースになります。

この例では、プロパティが変更されたときに、スライダーを動かすと、より正確にコマンドを<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>呼び出します。

クラス定義は次のとおりです。

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

次の手順では、メンバーを<xref:System.Windows.Input.ICommandSource>実装します。 この例では、プロパティはオブジェクトとして<xref:System.Windows.DependencyProperty>実装されています。 これにより、プロパティでデータ バインディングを使用できるようになります。 クラスの詳細については、「 <xref:System.Windows.DependencyProperty> [依存関係プロパティの概要](dependency-properties-overview.md)」を参照してください。 データ バインディングの詳細については、「 データ バインディングの[概要](../../../desktop-wpf/data/data-binding-overview.md)」を参照してください。

ここでは、<xref:System.Windows.Input.ICommandSource.Command%2A>プロパティのみが表示されます。

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
変更コールバックは<xref:System.Windows.DependencyProperty>次のとおりです。

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

次の手順では、コマンド ソースに関連付けられているコマンドを追加および削除します。 新<xref:System.Windows.Input.ICommandSource.Command%2A>しいコマンドが追加されたときに、プロパティを上書きすることはできません。

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

次の手順では、ハンドラーのロジックを<xref:System.Windows.Input.ICommand.CanExecuteChanged>作成します。

この<xref:System.Windows.Input.ICommand.CanExecuteChanged>イベントは、コマンドソースに、現在のコマンドターゲットで実行する機能が変更された可能性があることを通知します。 コマンド ソースはこのイベントを受け取ると、通常は<xref:System.Windows.Input.ICommand.CanExecute%2A>コマンドのメソッドを呼び出します。 コマンドが現在のコマンド ターゲットで実行できない場合、通常、コマンド ソースは無効になります。 コマンドが現在のコマンド ターゲットで実行できる場合、通常、コマンド ソースは自身を有効にします。

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

最後のステップは<xref:System.Windows.Input.ICommand.Execute%2A>メソッドです。 コマンドが<xref:System.Windows.Input.RoutedCommand>の場合、メソッド<xref:System.Windows.Input.RoutedCommand><xref:System.Windows.Input.RoutedCommand.Execute%2A>が呼び出されます。それ以外の<xref:System.Windows.Input.ICommand><xref:System.Windows.Input.ICommand.Execute%2A>場合は、メソッドが呼び出されます。

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [コマンド実行の概要](commanding-overview.md)
