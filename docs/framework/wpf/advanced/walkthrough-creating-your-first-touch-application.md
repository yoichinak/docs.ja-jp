---
title: 'チュートリアル: 初めてのタッチ アプリケーションの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
ms.openlocfilehash: 53ae737394d76d9f293f6e03fbf04cbb46d2adbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778821"
---
# <a name="walkthrough-creating-your-first-touch-application"></a>チュートリアル: 初めてのタッチ アプリケーションの作成
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] タッチに応答するアプリケーションを有効にします。 たとえば、いずれかを使用するアプリケーションとやり取りするまたはこのチュートリアルは、ユーザーに移動できるようにするアプリケーションを作成します。 タッチ スクリーンなどのタッチを検知するデバイスに複数の指がサイズ変更、またはタッチを使用して 1 つのオブジェクトを回転します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
- Visual Studio  
  
- Windows タッチをサポートするタッチ スクリーンなど、タッチ入力を受け取るデバイス。  
  
 アプリケーションを作成する方法の基本を理解しておくさらに、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、サブスクライブして、イベントを処理する方法に特にです。 詳細については、「[チュートリアル:初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)します。  
  
## <a name="creating-the-application"></a>アプリケーションの作成  
  
#### <a name="to-create-the-application"></a>アプリケーションを作成するには  
  
1. Visual Basic または Visual c# のという名前で新しい WPF アプリケーション プロジェクトを作成する`BasicManipulation`します。 詳細については、「[チュートリアル:初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)します。  
  
2. MainWindow.xaml の内容を次の XAML に置き換えます。  
  
     このマークアップは、赤いを含む単純なアプリケーションを作成します。<xref:System.Windows.Shapes.Rectangle>上、<xref:System.Windows.Controls.Canvas>します。 <xref:System.Windows.UIElement.IsManipulationEnabled%2A>のプロパティ、<xref:System.Windows.Shapes.Rectangle>操作イベントを受信するために true に設定されます。 アプリケーションをサブスクライブする、 <xref:System.Windows.UIElement.ManipulationStarting>、 <xref:System.Windows.UIElement.ManipulationDelta>、および<xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント。 これらのイベントに移動するためのロジックが含まれて、<xref:System.Windows.Shapes.Rectangle>ユーザーからの操作をすることです。  
  
     [!code-xaml[BasicManipulation#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3. Visual Basic では、MainWindow.xaml の最初の行でを使用している場合は置き換えます`x:Class="BasicManipulation.MainWindow"`で`x:Class="MainWindow"`します。  
  
4. `MainWindow`クラスで、次の追加<xref:System.Windows.UIElement.ManipulationStarting>イベント ハンドラー。  
  
     <xref:System.Windows.UIElement.ManipulationStarting>イベントが発生したときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]そのタッチを検出したオブジェクトを操作する入力を開始します。 コードでは、に対して相対的な操作の位置があることを指定します、<xref:System.Windows.Window>を設定して、<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>プロパティ。  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]

5. `MainWindow`クラスで、次の追加<xref:System.Windows.Input.ManipulationDelta>イベント ハンドラー。

     <xref:System.Windows.Input.ManipulationDelta>イベント、タッチ入力の位置を変更し、操作中に複数回発生する可能性があるときに発生します。 イベントは、指が発生した後にも発生します。 たとえば、ユーザーが、画面上に指をドラッグする場合、<xref:System.Windows.Input.ManipulationDelta>イベントでは、本の指の移動として複数回が発生します。 ユーザーが画面から指を生成するタイミング、<xref:System.Windows.Input.ManipulationDelta>慣性による処理をシミュレートするためにイベントが発生し続けます。

     コードが適用されます、<xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A>を<xref:System.Windows.UIElement.RenderTransform%2A>の<xref:System.Windows.Shapes.Rectangle>入力をユーザーがタッチを移動すると移動します。 確認するかどうか、<xref:System.Windows.Shapes.Rectangle>の境界の外側には、<xref:System.Windows.Window>慣性による処理中にイベントが発生します。 そのため、アプリケーションを呼び出す場合、<xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType>メソッドを操作を終了します。

     [!code-csharp[BasicManipulation#ManipulationDelta](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]

6. `MainWindow`クラスで、次の追加<xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント ハンドラー。

     <xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント、ユーザーが画面からすべての指を発生させるときに発生します。 コードでは、初期速度と移動、拡張、および四角形の回転角度の減速を設定します。

     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]

7. プロジェクトをビルドして実行します。

     ウィンドウに表示される赤色の四角形が表示されます。

## <a name="testing-the-application"></a>アプリケーションのテスト
 アプリケーションをテストするには、次の操作を再試行してください。 同時に、次の 1 つ以上実行できることに注意してください。

- 移動する、 <xref:System.Windows.Shapes.Rectangle>、に指を置き、<xref:System.Windows.Shapes.Rectangle>し、画面上で指を移動します。

- サイズを変更する、 <xref:System.Windows.Shapes.Rectangle>2 本の指を置く、<xref:System.Windows.Shapes.Rectangle>近い一緒または相互よりも、本の指を移動します。

- 回転する、 <xref:System.Windows.Shapes.Rectangle>2 本の指を置く、<xref:System.Windows.Shapes.Rectangle>を互いに指を回転させます。

 慣性による処理には、直前の操作を実行する際は、画面から指すばやくを発生させます。 <xref:System.Windows.Shapes.Rectangle>移動、サイズ変更、または停止する前に、数秒回転し続けます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>