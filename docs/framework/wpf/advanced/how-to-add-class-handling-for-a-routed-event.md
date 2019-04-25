---
title: '方法: ルーティング イベントのクラス処理を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 7b897954cbdab461dc0305c6290e67c1af5282c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224274"
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>方法: ルーティング イベントのクラス処理を追加する
クラス ハンドラーまたはルート内の特定のノード上のインスタンス ハンドラーによって、ルーティング イベントを処理できます。 クラス ハンドラーは、最初が呼び出され、インスタンスの処理からのイベントを抑制するか、基底クラスによって所有されているイベントに関するその他のイベント固有の動作を紹介するクラスの実装で使用できます。 この例では、クラス ハンドラーを実装するための 2 つの密接に関連する手法を示します。  
  
## <a name="example"></a>例  
 この例に基づいてカスタム クラスを使用して、<xref:System.Windows.Controls.Canvas>パネル。 アプリケーションの基本的な前提は、カスタム クラスが、マウスの左ボタンのクリックをインターセプトして的なマーキングの子要素のクラスまたはそれには、どのインスタンス ハンドラーが呼び出される前に、その処理を含め、その子要素上での動作が導入されています。  
  
 <xref:System.Windows.UIElement>クラスで処理できるようにする仮想メソッドを公開するクラス、<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>イベントを単にイベントをオーバーライドします。 これは、このような仮想メソッドがクラスの階層のどこかで利用できる場合は、クラス処理を実装する最も簡単な方法です。 次のコードは、 <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> "MyEditContainer"から派生した実装<xref:System.Windows.Controls.Canvas>します。 実装では、イベントを引数の処理済みとしてマークし、し、基本的な表示の変更を元の要素に与えるコードを追加します。  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 ユーティリティ メソッドを使用して直接クラス処理を追加できる仮想いいえが基底クラスまたはその特定のメソッドの使用可能な場合は、<xref:System.Windows.EventManager>クラス、<xref:System.Windows.EventManager.RegisterClassHandler%2A>します。 このメソッドは、クラス処理を追加しているクラスの静的な初期化内でのみ呼び出す必要があります。 この例の別のハンドラーを追加します<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>、ここで、登録済みのクラスは、カスタム クラスとします。 これに対し、仮想メソッドを使用する場合、登録済みのクラスは実際、<xref:System.Windows.UIElement>基本クラス。 基底クラスとサブクラスのクラス処理を登録する場所の場合、サブクラスのハンドラーが最初に呼び出されます。 アプリケーションの動作は、このハンドラーは、メッセージ ボックスを表示する最初と、仮想メソッドのハンドラーで視覚的変更し、表示されることになります。  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.EventManager>
- [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)
- [ルーティング イベントを処理する](how-to-handle-a-routed-event.md)
- [ルーティング イベントの概要](routed-events-overview.md)
