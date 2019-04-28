---
title: 'チュートリアル: ユーザー コントロールでのドラッグ アンド ドロップの有効化'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: a628665ccfa0a423667344b1fe81f132d6691b12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778923"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>チュートリアル: ユーザー コントロールでのドラッグ アンド ドロップの有効化

このチュートリアルでのドラッグ アンド ドロップのデータ転送に含めることができるカスタム ユーザー コントロールを作成する方法について説明[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。

このチュートリアルでは、カスタムの WPF を作成します<xref:System.Windows.Controls.UserControl>を表す円を選択します。 ドラッグ アンド ドロップを介したデータ転送を有効にするコントロールの機能を実装します。 たとえば、別に 1 つの円コントロールからドラッグすると、塗りつぶしの色のデータはターゲットにでコピーに円のソースから。 円のコントロールからドラッグした場合、 <xref:System.Windows.Controls.TextBox>、塗りつぶしの色の文字列形式にコピー、<xref:System.Windows.Controls.TextBox>します。 2 つのパネル コントロールを含む小さなアプリケーションを作成することも、および<xref:System.Windows.Controls.TextBox>ドラッグ アンド ドロップ機能をテストします。 パネルは、円を 1 つのパネルの子のコレクションから、もう一方にコピーまたは移動することが可能にする、ドロップされた円のデータを処理できるようにするコードを記述します。

このチュートリアルでは、次の作業について説明します。

- カスタム ユーザー コントロールを作成します。

- ドラッグ元にユーザー コントロールを有効にします。

- ドロップ ターゲットにするユーザー コントロールを有効にします。

- ユーザー コントロールから削除されるデータを受信するパネルを有効にします。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには Visual Studio が必要です。

## <a name="create-the-application-project"></a>アプリケーション プロジェクトを作成します。
 このセクションでは、2 つのパネルでのメイン ページを含むアプリケーション インフラストラクチャを作成します、<xref:System.Windows.Controls.TextBox>します。

1. Visual Basic または Visual c# のという名前で新しい WPF アプリケーション プロジェクトを作成する`DragDropExample`します。 詳細については、「[チュートリアル:初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)します。

2. MainWindow.xaml を開きます。

3. 開始タグと終了の間で、次のマークアップを追加<xref:System.Windows.Controls.Grid>タグ。

     このマークアップは、テスト アプリケーションのユーザー インターフェイスを作成します。

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>プロジェクトに新しいユーザー コントロールを追加します。
 このセクションでは、プロジェクトに新しいユーザー コントロールを追加します。

1. [プロジェクト] メニューで、次のように選択します。**ユーザー コントロールの追加**します。

2. **新しい項目の追加** ダイアログ ボックスで、名を変更して`Circle.xaml`、 をクリック**追加**します。

     Circle.xaml とその分離コードは、プロジェクトに追加されます。

3. Circle.xaml を開きます。

     このファイルは、ユーザー コントロールのユーザー インターフェイス要素が格納されます。

4. ルートに次のマークアップを追加<xref:System.Windows.Controls.Grid>シンプルなユーザー コントロールがその UI として、青色の円を作成します。

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. Circle.xaml.cs または Circle.xaml.vb を開きます。

6. C# では、コピー コンス トラクターを作成する既定のコンス トラクターの後に次のコードを追加します。 Visual basic では、既定のコンス トラクターとコピー コンス トラクターの両方を作成するには、次のコードを追加します。

     コピーするユーザー コントロールを許可するためには、分離コード ファイルのコピー コンス トラクター メソッドを追加します。 簡略化された円ユーザー コントロールではのみをコピーする、塗りつぶしとのサイズ、ユーザー コントロールの。

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>メイン ウィンドウに、ユーザー コントロールを追加します。

1. MainWindow.xaml を開きます。

2. 開始する次の XAML を追加<xref:System.Windows.Window>タグが現在のアプリケーションに XML 名前空間参照を作成します。

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. 最初の<xref:System.Windows.Controls.StackPanel>、最初のパネルで、円のユーザー コントロールの 2 つのインスタンスを作成する次の XAML を追加します。

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     パネルの完全な XAML は、次のようになります。

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>ユーザー コントロールでドラッグ ソースのイベントを実装します。
 このセクションでをオーバーライドして、<xref:System.Windows.UIElement.OnMouseMove%2A>メソッドと、ドラッグ アンド ドロップ操作を開始します。

 ドラッグを開始する場合 (マウス ボタンが押され、マウスを移動) に転送されるデータをパッケージ化は、<xref:System.Windows.DataObject>します。 ここでは、円コントロールが; 3 つのデータ項目をパッケージします。塗りつぶしの色、高さの二重表現自体のコピーの文字列表現。

### <a name="to-initiate-a-drag-and-drop-operation"></a>ドラッグ アンド ドロップ操作を開始するには

1. Circle.xaml.cs または Circle.xaml.vb を開きます。

2. 次の追加<xref:System.Windows.UIElement.OnMouseMove%2A>のクラス処理を提供するオーバーライド、<xref:System.Windows.UIElement.MouseMove>イベント。

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     これは、<xref:System.Windows.UIElement.OnMouseMove%2A>オーバーライドは、次のタスクを実行します。

    - マウスが移動中に、マウスの左ボタンが押されたかどうかを確認します。

    - パッケージにデータを円、<xref:System.Windows.DataObject>します。 この場合、円コントロール パッケージを 3 つのデータ項目。塗りつぶしの色、高さの二重表現自体のコピーの文字列表現。

    - 静的な呼び出し<xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>ドラッグ アンド ドロップ操作を開始するメソッド。 次の 3 つのパラメーターを渡す、<xref:System.Windows.DragDrop.DoDragDrop%2A>メソッド。

        - `dragSource` – このコントロールへの参照。

        - `data` –<xref:System.Windows.DataObject>前のコードで作成します。

        - `allowedEffects` – の許可されているドラッグ アンド ドロップ操作<xref:System.Windows.DragDropEffects.Copy>または<xref:System.Windows.DragDropEffects.Move>します。

3. **F5** キーを押してアプリケーションをビルドし、実行します。

4. 円のコントロールのいずれかをクリックし、パネル、他の円をドラッグし、<xref:System.Windows.Controls.TextBox>します。 ドラッグしたとき、<xref:System.Windows.Controls.TextBox>カーソルが移動を示すために変わります。

5. 経由で円をドラッグするときに、 <xref:System.Windows.Controls.TextBox>、キーを押して、 **Ctrl**キー。 コピーを示すために、カーソルの変更に注意してください。

6. ドラッグ アンド ドロップ上の円、<xref:System.Windows.Controls.TextBox>します。 円の塗りつぶしの色の文字列表現を追加、<xref:System.Windows.Controls.TextBox>します。

     ![円の塗りつぶしの色の文字列表現](./media/dragdrop-colorstring.png "DragDrop_ColorString")

既定では、カーソルは、どのようなデータを削除する効果を持つが示すにドラッグ アンド ドロップ操作中に変更されます。 処理することにより、ユーザーにフィードバックをカスタマイズすることができます、<xref:System.Windows.UIElement.GiveFeedback>イベントと異なるカーソルを設定します。

## <a name="give-feedback-to-the-user"></a>ユーザーにフィードバックします。

1. Circle.xaml.cs または Circle.xaml.vb を開きます。

2. 次の追加<xref:System.Windows.UIElement.OnGiveFeedback%2A>のクラス処理を提供するオーバーライド、<xref:System.Windows.UIElement.GiveFeedback>イベント。

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     これは、<xref:System.Windows.UIElement.OnGiveFeedback%2A>オーバーライドは、次のタスクを実行します。

    - チェック、<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>でドロップ先の設定されている値<xref:System.Windows.UIElement.DragOver>イベント ハンドラー。

    - 基づくカスタム カーソル設定、<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>値。 カーソルは、どのようなデータを削除する効果は必要があります。 詳細については、ユーザーに視覚的なフィードバックを提供するものです。

3. **F5** キーを押してアプリケーションをビルドし、実行します。

4. 円の 1 つを管理パネル、他の円の上をドラッグし、<xref:System.Windows.Controls.TextBox>します。 カーソルがで指定したカスタム カーソル、<xref:System.Windows.UIElement.OnGiveFeedback%2A>をオーバーライドします。

     ![カスタム カーソルによるドラッグ アンド ドロップ](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5. テキスト選択`green`から、<xref:System.Windows.Controls.TextBox>します。

6. ドラッグ、`green`円コントロールにテキスト。 ドラッグ アンド ドロップ操作の効果を示すために既定のカーソルが表示されることに注意してください。 フィードバックのカーソルは、ドラッグ ソースが常に設定されます。

## <a name="implement-drop-target-events-in-the-user-control"></a>ユーザー コントロールのドロップ先のイベントを実装します。
 このセクションでは、ユーザー コントロールがドロップ ターゲットでは、上書き、ユーザーを有効にするメソッドは、ドロップ先を制御し、その上にドロップしたデータを処理であるかを指定します。

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>ドロップ ターゲットにするユーザー コントロールを有効にするには

1. Circle.xaml を開きます。

2. オープンで<xref:System.Windows.Controls.UserControl>タグを追加、<xref:System.Windows.UIElement.AllowDrop%2A>プロパティに設定し、`true`します。

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<xref:System.Windows.UIElement.OnDrop%2A>メソッドが呼び出されます、<xref:System.Windows.UIElement.AllowDrop%2A>プロパティに設定されて`true`円ユーザー コントロールでドラッグ ソースからデータが削除されるとします。 このメソッドでは、ドロップされたデータを処理し、データを円に適用します。

### <a name="to-process-the-dropped-data"></a>削除されたデータを処理する

1. Circle.xaml.cs または Circle.xaml.vb を開きます。

2. 次の追加<xref:System.Windows.UIElement.OnDrop%2A>のクラス処理を提供するオーバーライド、<xref:System.Windows.UIElement.Drop>イベント。

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     これは、<xref:System.Windows.UIElement.OnDrop%2A>オーバーライドは、次のタスクを実行します。

    - 使用して、<xref:System.Windows.DataObject.GetDataPresent%2A>ドラッグ中のデータに文字列オブジェクトが含まれているかどうかをチェックするメソッド。

    - 使用して、<xref:System.Windows.DataObject.GetData%2A>メソッドが存在する場合は、文字列データを抽出します。

    - 使用して、<xref:System.Windows.Media.BrushConverter>を文字列に変換しようとする、<xref:System.Windows.Media.Brush>します。

    - 変換が成功した場合は、適用するブラシ、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>円コントロールの UI を提供します。

    - マーク、<xref:System.Windows.UIElement.Drop>イベントを処理します。 このイベントを受信する他の要素が円のユーザー コントロールに処理を認識できるように処理済みとしてドロップ イベントをマークする必要があります。

3. **F5** キーを押してアプリケーションをビルドし、実行します。

4. テキスト選択`green`で、<xref:System.Windows.Controls.TextBox>します。

5. 円のコントロールにテキストをドラッグし、ドロップします。 円は、青から緑に変更します。

     ![文字列、ブラシを変換](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6. テキスト入力`green`で、<xref:System.Windows.Controls.TextBox>します。

7. テキスト選択`gre`で、<xref:System.Windows.Controls.TextBox>します。

8. 円のコントロールにドラッグし、ドロップします。 カーソルの変化を示すために、円の色が変更されませんが、ドロップは許可されて`gre`は有効な色ではありません。

9. 緑色の円のコントロールをドラッグし、青い円コントロールにドロップします。 円は、青から緑に変更します。 カーソルが表示されるかどうかによって異なりますが、<xref:System.Windows.Controls.TextBox>円はドラッグ元であるか。

設定、<xref:System.Windows.UIElement.AllowDrop%2A>プロパティを`true`要素になるドロップ ターゲットを有効にするために必要なは、ドロップしたデータを処理します。 ただし、優れたユーザー エクスペリエンスを提供する必要がありますも処理する、 <xref:System.Windows.UIElement.DragEnter>、 <xref:System.Windows.UIElement.DragLeave>、および<xref:System.Windows.UIElement.DragOver>イベント。 これらのイベントでは、チェックを実行し、データが削除される前に、追加のフィードバックをユーザーに提供できます。

データが円のユーザー コントロールの上にドラッグされるときに、コントロールはドラッグされているデータを処理するかどうか、ドラッグ元で通知する必要があります。 コントロールにデータを処理する方法を把握していない場合、削除を拒否する必要があります。 処理するのには、<xref:System.Windows.UIElement.DragOver>イベントとセット、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティ。

### <a name="to-verify-that-the-data-drop-is-allowed"></a>データの削除が許可されていることを確認するには

1. Circle.xaml.cs または Circle.xaml.vb を開きます。

2. 次の追加<xref:System.Windows.UIElement.OnDragOver%2A>のクラス処理を提供するオーバーライド、<xref:System.Windows.UIElement.DragOver>イベント。

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     これは、<xref:System.Windows.UIElement.OnDragOver%2A>オーバーライドは、次のタスクを実行します。

    - <xref:System.Windows.DragEventArgs.Effects%2A> プロパティを <xref:System.Windows.DragDropEffects.None> に設定します。

    - 実行される同じチェックが実行、<xref:System.Windows.UIElement.OnDrop%2A>円ユーザー コントロールがドラッグしたデータを処理できるかどうかを判断するメソッド。

    - ユーザー コントロールには、データを処理できますが、設定、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティを<xref:System.Windows.DragDropEffects.Copy>または<xref:System.Windows.DragDropEffects.Move>します。

3. **F5** キーを押してアプリケーションをビルドし、実行します。

4. テキスト選択`gre`で、<xref:System.Windows.Controls.TextBox>します。

5. 円のコントロールにテキストをドラッグします。 カーソルが今すぐに変化を示すため、ドロップは許可されません`gre`は有効な色ではありません。

 ドロップ操作のプレビューを適用することで、ユーザー エクスペリエンスをさらに強化できます。 オーバーライド円ユーザー コントロールの場合、<xref:System.Windows.UIElement.OnDragEnter%2A>と<xref:System.Windows.UIElement.OnDragLeave%2A>メソッド。 データが、コントロールの現在の背景上にドラッグされるときに<xref:System.Windows.Shapes.Shape.Fill%2A>プレース ホルダー変数に保存されます。 文字列は、ブラシに変換されに適用される、<xref:System.Windows.Shapes.Ellipse>円を提供する UI。 データが元、ドロップされることがなく円からドラッグした場合<xref:System.Windows.Shapes.Shape.Fill%2A>値は円に再適用されます。

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>ドラッグ アンド ドロップ操作の効果をプレビューするには

1. Circle.xaml.cs または Circle.xaml.vb を開きます。

2. 円クラスで宣言プライベート<xref:System.Windows.Media.Brush>という名前の変数`_previousFill`し初期化`null`します。

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. 次の追加<xref:System.Windows.UIElement.OnDragEnter%2A>のクラス処理を提供するオーバーライド、<xref:System.Windows.UIElement.DragEnter>イベント。

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     これは、<xref:System.Windows.UIElement.OnDragEnter%2A>オーバーライドは、次のタスクを実行します。

    - 保存、<xref:System.Windows.Shapes.Shape.Fill%2A>のプロパティ、<xref:System.Windows.Shapes.Ellipse>で、`_previousFill`変数。

    - 実行される同じチェックが実行、<xref:System.Windows.UIElement.OnDrop%2A>にデータを変換できるかどうかを判断するメソッド、<xref:System.Windows.Media.Brush>します。

    - 有効なデータが変換される場合<xref:System.Windows.Media.Brush>、それを適用、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>します。

4. 次の追加<xref:System.Windows.UIElement.OnDragLeave%2A>のクラス処理を提供するオーバーライド、<xref:System.Windows.UIElement.DragLeave>イベント。

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     これは、<xref:System.Windows.UIElement.OnDragLeave%2A>オーバーライドは、次のタスクを実行します。

    - 適用される、<xref:System.Windows.Media.Brush>に保存されている、`_previousFill`変数を<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>円ユーザー コントロールの UI を提供します。

5. **F5** キーを押してアプリケーションをビルドし、実行します。

6. テキスト選択`green`で、<xref:System.Windows.Controls.TextBox>します。

7. 円のコントロールを削除しないテキストをドラッグします。 円は、青から緑に変更します。

     ![ドラッグの効果のプレビュー&#45;と&#45;ドロップ操作](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8. 円コントロールからテキストをドラッグします。 円を青に緑色のバックアップから変更します。

## <a name="enable-a-panel-to-receive-dropped-data"></a>ドロップしたデータを受信するパネルを有効にします。

このセクションでは、円のドラッグしたデータのドロップ ターゲットとして機能する円のユーザー コントロールをホストするパネルを有効にします。 円を別の 1 つのパネルに移動するかを押しながら Circle コントロールのコピーを作成することができるコードを実装する、 **Ctrl**ドラッグ アンド ドロップ、円の中にキー。

1. MainWindow.xaml を開きます。

2. それぞれで、次の XAML に示すように、<xref:System.Windows.Controls.StackPanel>のハンドラーの追加、コントロール、<xref:System.Windows.UIElement.DragOver>と<xref:System.Windows.UIElement.Drop>イベント。 名前、<xref:System.Windows.UIElement.DragOver>イベント ハンドラー、 `panel_DragOver`、し、名前、<xref:System.Windows.UIElement.Drop>イベント ハンドラー、`panel_Drop`します。

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. MainWindows.xaml.cs または MainWindow.xaml.vb を開きます。

4. 次のコードを追加、<xref:System.Windows.UIElement.DragOver>イベント ハンドラー。

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     これは、<xref:System.Windows.UIElement.DragOver>イベント ハンドラーは、次のタスクを実行します。

    - パッケージ化された「オブジェクト」のデータにはドラッグしたデータが含まれているを確認します、<xref:System.Windows.DataObject>円のユーザー コントロールへの呼び出しで渡されると<xref:System.Windows.DragDrop.DoDragDrop%2A>します。

    - 「オブジェクト」のデータが存在する場合、チェックするかどうか、 **Ctrl**キーが押されました。

    - 場合、 **Ctrl**キーを押す、セット、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティを<xref:System.Windows.DragDropEffects.Copy>します。 それ以外の場合、設定、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティを<xref:System.Windows.DragDropEffects.Move>します。

5. 次のコードを追加、<xref:System.Windows.UIElement.Drop>イベント ハンドラー。

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     これは、<xref:System.Windows.UIElement.Drop>イベント ハンドラーは、次のタスクを実行します。

    - チェックするかどうか、<xref:System.Windows.UIElement.Drop>イベントが既に処理されました。 別の円が削除された場合 Circle をたとえば、ハンドル、<xref:System.Windows.UIElement.Drop>イベント、たくも処理する円形を格納しているパネル。

    - 場合、<xref:System.Windows.UIElement.Drop>イベントが処理されない、チェックするかどうか、 **Ctrl**キーが押されました。

    - 場合、 **Ctrl**キーが押されたときに、<xref:System.Windows.UIElement.Drop>が発生し、制御が円のコピーに追加、<xref:System.Windows.Controls.Panel.Children%2A>のコレクション、<xref:System.Windows.Controls.StackPanel>します。

    - 場合、 **Ctrl**から円を移動キーが押されていない、<xref:System.Windows.Controls.Panel.Children%2A>をその親パネルのコレクション、<xref:System.Windows.Controls.Panel.Children%2A>上にドロップされたパネルのコレクション。

    - セット、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティに通知する、<xref:System.Windows.DragDrop.DoDragDrop%2A>メソッドを移動またはコピー操作が実行されたかどうか。

6. **F5** キーを押してアプリケーションをビルドし、実行します。

7. テキスト選択`green`から、<xref:System.Windows.Controls.TextBox>します。

8. 円のコントロールの上のテキストをドラッグし、ドロップします。

9. 右側のパネルの左側のパネルから円コントロールをドラッグし、ドロップします。 円はから削除、<xref:System.Windows.Controls.Panel.Children%2A>左側のパネルのコレクションと、右側のパネルの子のコレクションに追加します。

10. その他のパネル内にあるパネルから円コントロールをドラッグし、キーを押しながらドロップ、 **Ctrl**キー。 円がコピーされ、コピーに追加されます、<xref:System.Windows.Controls.Panel.Children%2A>受信側のパネルのコレクション。

     ![CTRL キーを押しながら Circle をドラッグ](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>関連項目

- [ドラッグ アンド ドロップの概要](drag-and-drop-overview.md)