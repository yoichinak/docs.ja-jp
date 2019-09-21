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
ms.openlocfilehash: 172e49c2c255db4d24d2180f919b1305326b5e82
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991809"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>チュートリアル: ユーザー コントロールでのドラッグ アンド ドロップの有効化

このチュートリアルでは、で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ドラッグアンドドロップデータ転送に参加できるカスタムユーザーコントロールを作成する方法について説明します。

このチュートリアルでは、円図形を表すカスタム<xref:System.Windows.Controls.UserControl> WPF を作成します。 ドラッグアンドドロップによるデータ転送を可能にするために、コントロールに機能を実装します。 たとえば、ある円コントロールから別のコントロールにドラッグすると、塗りつぶしの色データがソースの円からターゲットにコピーされます。 円コントロール<xref:System.Windows.Controls.TextBox>からにドラッグすると、塗りつぶしの色の文字列形式がにコピー <xref:System.Windows.Controls.TextBox>されます。 また、2つのパネルコントロールと、を<xref:System.Windows.Controls.TextBox>使用してドラッグアンドドロップ機能をテストする小さなアプリケーションも作成します。 パネルがドロップされた円データを処理できるようにするコードを記述します。これにより、あるパネルの子コレクションから別のパネルに円を移動またはコピーすることができます。

このチュートリアルでは、次の作業について説明します。

- カスタムユーザーコントロールを作成します。

- ユーザーコントロールがドラッグ元になるようにします。

- ユーザーコントロールをドロップ先として有効にします。

- パネルで、ユーザーコントロールから削除されたデータを受信できるようにします。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには Visual Studio が必要です。

## <a name="create-the-application-project"></a>アプリケーションプロジェクトを作成する
 このセクションでは、2つのパネルとを<xref:System.Windows.Controls.TextBox>持つメインページを含むアプリケーションインフラストラクチャを作成します。

1. Visual Basic またはという名前C# `DragDropExample`のビジュアルで新しい WPF アプリケーションプロジェクトを作成します。 詳細については、「[チュートリアル:初めての WPF デスクトップ](../getting-started/walkthrough-my-first-wpf-desktop-application.md)アプリケーション。

2. MainWindow.xaml を開きます。

3. 開始タグと終了<xref:System.Windows.Controls.Grid>タグの間に次のマークアップを追加します。

     このマークアップは、テストアプリケーションのユーザーインターフェイスを作成します。

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>新しいユーザーコントロールをプロジェクトに追加する
 このセクションでは、新しいユーザーコントロールをプロジェクトに追加します。

1. プロジェクト メニューの **ユーザーコントロールの追加** をクリックします。

2. **[新しい項目の追加]** ダイアログボックスで、名前を`Circle.xaml`に変更し、 **[追加]** をクリックします。

     Circle .xaml とその分離コードがプロジェクトに追加されます。

3. [Circle .xaml] を開きます。

     このファイルには、ユーザーコントロールのユーザーインターフェイス要素が含まれます。

4. 次のマークアップをルート<xref:System.Windows.Controls.Grid>に追加して、UI として青い円を持つ単純なユーザーコントロールを作成します。

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. Circle.xaml.cs または Circle .xaml を開きます。

6. でC#、パラメーターなしのコンストラクターの後に次のコードを追加して、コピーコンストラクターを作成します。 Visual Basic で、次のコードを追加して、パラメーターなしのコンストラクターとコピーコンストラクターの両方を作成します。

     ユーザーコントロールのコピーを許可するには、分離コードファイルにコピーコンストラクターメソッドを追加します。 簡略化された円ユーザーコントロールでは、ユーザーコントロールのの塗りつぶしとサイズのみをコピーします。

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>メインウィンドウにユーザーコントロールを追加する

1. MainWindow.xaml を開きます。

2. 次の XAML を開始<xref:System.Windows.Window>タグに追加して、現在のアプリケーションへの XML 名前空間参照を作成します。

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. 最初<xref:System.Windows.Controls.StackPanel>のパネルで、次の XAML を追加して、円ユーザーコントロールのインスタンスを2つ作成します。

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     パネルの完全な XAML は次のようになります。

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>ユーザーコントロールでのドラッグソースイベントの実装
 このセクションでは、 <xref:System.Windows.UIElement.OnMouseMove%2A>メソッドをオーバーライドし、ドラッグアンドドロップ操作を開始します。

 ドラッグが開始された場合 (マウスボタンが押された状態でマウスが移動された場合)、に転送<xref:System.Windows.DataObject>されるデータをパッケージ化します。 この場合、円コントロールは3つのデータ項目をパッケージ化します。塗りつぶしの色の文字列形式、その高さを示す double 表現、およびそれ自体のコピー。

### <a name="to-initiate-a-drag-and-drop-operation"></a>ドラッグアンドドロップ操作を開始するには

1. Circle.xaml.cs または Circle .xaml を開きます。

2. 次<xref:System.Windows.UIElement.OnMouseMove%2A>のオーバーライドを追加して、 <xref:System.Windows.UIElement.MouseMove>イベントのクラス処理を提供します。

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     この<xref:System.Windows.UIElement.OnMouseMove%2A>オーバーライドは、次のタスクを実行します。

    - マウスの移動中にマウスの左ボタンが押されたかどうかを確認します。

    - 円データ<xref:System.Windows.DataObject>をにパッケージ化します。 この場合、円コントロールは3つのデータ項目をパッケージ化します。塗りつぶしの色の文字列形式、その高さを示す double 表現、およびそれ自体のコピー。

    - 静的<xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>メソッドを呼び出して、ドラッグアンドドロップ操作を開始します。 次の3つのパラメーターを<xref:System.Windows.DragDrop.DoDragDrop%2A>メソッドに渡します。

        - `dragSource`–このコントロールへの参照。

        - `data`–前のコードで作成された。<xref:System.Windows.DataObject>

        - `allowedEffects`–使用できるドラッグアンドドロップ操作。これ<xref:System.Windows.DragDropEffects.Copy>は、または<xref:System.Windows.DragDropEffects.Move>です。

3. **F5** キーを押してアプリケーションをビルドし、実行します。

4. 円コントロールのいずれかをクリックし、パネル、もう一方の円、およびに<xref:System.Windows.Controls.TextBox>ドラッグします。 上<xref:System.Windows.Controls.TextBox>にドラッグすると、カーソルは移動を示すように変更されます。

5. 上<xref:System.Windows.Controls.TextBox>に円をドラッグしているときに、 **ctrl**キーを押します。 カーソルがコピーを示すように変更されていることに注目してください。

6. 円をに<xref:System.Windows.Controls.TextBox>ドラッグアンドドロップします。 円の塗りつぶしの色の文字列形式がに<xref:System.Windows.Controls.TextBox>追加されます。

     ![円の塗りつぶしの色の文字列表現](./media/dragdrop-colorstring.png "DragDrop_ColorString")

既定では、カーソルはドラッグアンドドロップ操作中に変更され、データの削除による影響を示します。 <xref:System.Windows.UIElement.GiveFeedback>イベントを処理し、別のカーソルを設定することによって、ユーザーに与えられたフィードバックをカスタマイズできます。

## <a name="give-feedback-to-the-user"></a>ユーザーへのフィードバックの提供

1. Circle.xaml.cs または Circle .xaml を開きます。

2. 次<xref:System.Windows.UIElement.OnGiveFeedback%2A>のオーバーライドを追加して、 <xref:System.Windows.UIElement.GiveFeedback>イベントのクラス処理を提供します。

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     この<xref:System.Windows.UIElement.OnGiveFeedback%2A>オーバーライドは、次のタスクを実行します。

    - ドロップ先の<xref:System.Windows.UIElement.DragOver>イベントハンドラーで設定されている値を確認します。<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>

    - <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>値に基づいてカスタムカーソルを設定します。 カーソルは、データの削除による影響についてユーザーに視覚的フィードバックを提供することを目的としています。

3. **F5** キーを押してアプリケーションをビルドし、実行します。

4. 円コントロールの1つを、パネル、もう一方の円、およびに<xref:System.Windows.Controls.TextBox>ドラッグします。 カーソルが、 <xref:System.Windows.UIElement.OnGiveFeedback%2A>オーバーライドで指定したカスタムカーソルになっていることに注意してください。

     ![カスタムカーソルを使用したドラッグアンドドロップ](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5. からテキスト`green`を選択します。<xref:System.Windows.Controls.TextBox>

6. `green`テキストを円コントロールにドラッグします。 ドラッグアンドドロップ操作の効果を示すために、既定のカーソルが表示されていることに注意してください。 フィードバックカーソルは、常にドラッグソースによって設定されます。

## <a name="implement-drop-target-events-in-the-user-control"></a>ユーザーコントロールにドロップ先のイベントを実装する
 このセクションでは、ユーザーコントロールがドロップ先であることを指定し、ユーザーコントロールをドロップ先として使用できるようにするメソッドをオーバーライドして、削除されたデータを処理します。

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>ユーザーコントロールをドロップ先として有効にするには

1. [Circle .xaml] を開きます。

2. 開始<xref:System.Windows.Controls.UserControl>タグに<xref:System.Windows.UIElement.AllowDrop%2A>プロパティを追加し、をに`true`設定します。

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

メソッドは、 <xref:System.Windows.UIElement.AllowDrop%2A>プロパティがに`true`設定され、ドラッグ元のデータが円ユーザーコントロールにドロップされたときに呼び出されます。 <xref:System.Windows.UIElement.OnDrop%2A> この方法では、削除されたデータを処理し、そのデータを円に適用します。

### <a name="to-process-the-dropped-data"></a>削除されたデータを処理するには

1. Circle.xaml.cs または Circle .xaml を開きます。

2. 次<xref:System.Windows.UIElement.OnDrop%2A>のオーバーライドを追加して、 <xref:System.Windows.UIElement.Drop>イベントのクラス処理を提供します。

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     この<xref:System.Windows.UIElement.OnDrop%2A>オーバーライドは、次のタスクを実行します。

    - <xref:System.Windows.DataObject.GetDataPresent%2A>メソッドを使用して、ドラッグされたデータに文字列オブジェクトが含まれているかどうかを確認します。

    - <xref:System.Windows.DataObject.GetData%2A>メソッドを使用して、文字列データが存在する場合はそれを抽出します。

    - を使用して、文字列<xref:System.Windows.Media.Brush>をに変換しようとします。 <xref:System.Windows.Media.BrushConverter>

    - 変換が成功した場合、は、円コントロール<xref:System.Windows.Shapes.Shape.Fill%2A>の UI <xref:System.Windows.Shapes.Ellipse>を提供するのにブラシを適用します。

    - イベントを<xref:System.Windows.UIElement.Drop>処理済みとしてマークします。 このイベントを受信する他の要素が、Circle ユーザーコントロールによって処理されたことを認識するように、drop イベントを処理済みとしてマークする必要があります。

3. **F5** キーを押してアプリケーションをビルドし、実行します。

4. でテキスト`green`を選択します。<xref:System.Windows.Controls.TextBox>

5. テキストを円コントロールにドラッグしてドロップします。 円が青から緑に変わります。

     ![文字列をブラシに変換する](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6. にテキスト`green`を入力します。<xref:System.Windows.Controls.TextBox>

7. でテキスト`gre`を選択します。<xref:System.Windows.Controls.TextBox>

8. それを円コントロールにドラッグしてドロップします。 カーソルはドロップが許可されていることを示すために変更されますが、は有効な`gre`色ではないため、円の色は変化しません。

9. 緑の円コントロールからドラッグし、青い円コントロールにドロップします。 円が青から緑に変わります。 どのカーソルが表示されるかは、 <xref:System.Windows.Controls.TextBox>または円がドラッグ元であるかどうかによって異なります。

要素をドロップターゲット`true`にできるようにするには、プロパティをに設定し、削除されたデータを処理する必要があります。<xref:System.Windows.UIElement.AllowDrop%2A> ただし、より優れたユーザーエクスペリエンスを提供するには、、 <xref:System.Windows.UIElement.DragEnter> <xref:System.Windows.UIElement.DragLeave>、および<xref:System.Windows.UIElement.DragOver>の各イベントも処理する必要があります。 これらのイベントでは、データを削除する前に、チェックを実行し、ユーザーに追加のフィードバックを提供することができます。

データが円のユーザーコントロール上にドラッグされると、ドラッグ元に対して、ドラッグされているデータを処理できるかどうかを通知する必要があります。 コントロールがデータの処理方法を認識していない場合は、削除を拒否する必要があります。 これを行うには、 <xref:System.Windows.UIElement.DragOver>イベントを処理し、 <xref:System.Windows.DragEventArgs.Effects%2A>プロパティを設定します。

### <a name="to-verify-that-the-data-drop-is-allowed"></a>データの削除が許可されていることを確認するには

1. Circle.xaml.cs または Circle .xaml を開きます。

2. 次<xref:System.Windows.UIElement.OnDragOver%2A>のオーバーライドを追加して、 <xref:System.Windows.UIElement.DragOver>イベントのクラス処理を提供します。

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     この<xref:System.Windows.UIElement.OnDragOver%2A>オーバーライドは、次のタスクを実行します。

    - <xref:System.Windows.DragEventArgs.Effects%2A> プロパティを <xref:System.Windows.DragDropEffects.None> に設定します。

    - は、円ユーザーコントロールがドラッグされ<xref:System.Windows.UIElement.OnDrop%2A>たデータを処理できるかどうかを判断するために、メソッドで実行されるのと同じチェックを実行します。

    - ユーザーコントロールがデータを処理できる場合は、 <xref:System.Windows.DragEventArgs.Effects%2A>プロパティをまたは<xref:System.Windows.DragDropEffects.Move>に<xref:System.Windows.DragDropEffects.Copy>設定します。

3. **F5** キーを押してアプリケーションをビルドし、実行します。

4. でテキスト`gre`を選択します。<xref:System.Windows.Controls.TextBox>

5. テキストを円コントロールにドラッグします。 が有効な色ではないため`gre` 、カーソルが変更されていないことを示すようになりました。

 削除操作のプレビューを適用することで、ユーザーエクスペリエンスをさらに向上させることができます。 Circle ユーザーコントロールでは、メソッド<xref:System.Windows.UIElement.OnDragEnter%2A>と<xref:System.Windows.UIElement.OnDragLeave%2A>メソッドをオーバーライドします。 データをコントロールの上にドラッグすると、現在の<xref:System.Windows.Shapes.Shape.Fill%2A>背景がプレースホルダー変数に保存されます。 次に、文字列がブラシに変換され、 <xref:System.Windows.Shapes.Ellipse>円の UI を提供するに適用されます。 データが削除されずに円の外にドラッグされた<xref:System.Windows.Shapes.Shape.Fill%2A>場合、元の値は円に再適用されます。

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>ドラッグアンドドロップ操作の効果をプレビューするには

1. Circle.xaml.cs または Circle .xaml を開きます。

2. Circle クラスで、という名前<xref:System.Windows.Media.Brush> `_previousFill`のプライベート変数を宣言し、 `null`それをに初期化します。

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. 次<xref:System.Windows.UIElement.OnDragEnter%2A>のオーバーライドを追加して、 <xref:System.Windows.UIElement.DragEnter>イベントのクラス処理を提供します。

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     この<xref:System.Windows.UIElement.OnDragEnter%2A>オーバーライドは、次のタスクを実行します。

    - のプロパティ<xref:System.Windows.Shapes.Shape.Fill%2A>を`_previousFill`変数に保存します。 <xref:System.Windows.Shapes.Ellipse>

    - <xref:System.Windows.UIElement.OnDrop%2A> は<xref:System.Windows.Media.Brush>、データをに変換できるかどうかを判断するために、メソッドで実行されるのと同じチェックを実行します。

    - データが有効<xref:System.Windows.Media.Brush>なに変換される場合は、 <xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>に適用されます。

4. 次<xref:System.Windows.UIElement.OnDragLeave%2A>のオーバーライドを追加して、 <xref:System.Windows.UIElement.DragLeave>イベントのクラス処理を提供します。

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     この<xref:System.Windows.UIElement.OnDragLeave%2A>オーバーライドは、次のタスクを実行します。

    - 変数`_previousFill` に保存<xref:System.Windows.Media.Brush>されているを、Circle ユーザーコントロールの UI を提供するのに適用します。<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Shapes.Shape.Fill%2A>

5. **F5** キーを押してアプリケーションをビルドし、実行します。

6. でテキスト`green`を選択します。<xref:System.Windows.Controls.TextBox>

7. テキストを削除せずに、円コントロールの上にドラッグします。 円が青から緑に変わります。

     ![&#45;&#45;ドラッグアンドドロップ操作の効果をプレビューする](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8. 円コントロールからテキストをドラッグします。 円が緑から青に変わります。

## <a name="enable-a-panel-to-receive-dropped-data"></a>パネルでドロップされたデータを受信できるようにする

このセクションでは、円のユーザーコントロールをホストするパネルを、ドラッグした円データのドロップターゲットとして機能するように有効にします。 1つのパネルから別のパネルに円を移動したり、円をドラッグアンドドロップしながら**Ctrl**キーを押しながら円コントロールのコピーを作成したりできるようにするコードを実装します。

1. MainWindow.xaml を開きます。

2. 次の XAML に示すように、各<xref:System.Windows.Controls.StackPanel>コントロールで、イベント<xref:System.Windows.UIElement.DragOver>と<xref:System.Windows.UIElement.Drop>イベントのハンドラーを追加します。 イベント<xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop>ハンドラーにという名前を指定し、イベントハンドラー `panel_Drop`にという名前を指定します。 `panel_DragOver`

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. MainWindows.xaml.cs または Mainwindow.xaml を開きます。

4. <xref:System.Windows.UIElement.DragOver>イベントハンドラーに次のコードを追加します。

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     この<xref:System.Windows.UIElement.DragOver>イベントハンドラーは、次のタスクを実行します。

    - ドラッグされたデータに、円ユーザーコントロールによってにパッケージさ<xref:System.Windows.DataObject>れ、の<xref:System.Windows.DragDrop.DoDragDrop%2A>呼び出しに渡された "オブジェクト" データが含まれていることを確認します。

    - "オブジェクト" データが存在する場合は、 **Ctrl**キーが押されたかどうかを確認します。

    - **Ctrl**キーが押されている場合は<xref:System.Windows.DragEventArgs.Effects%2A> 、プロパティ<xref:System.Windows.DragDropEffects.Copy>をに設定します。 それ以外の場合<xref:System.Windows.DragEventArgs.Effects%2A>は、 <xref:System.Windows.DragDropEffects.Move>プロパティをに設定します。

5. <xref:System.Windows.UIElement.Drop>イベントハンドラーに次のコードを追加します。

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     この<xref:System.Windows.UIElement.Drop>イベントハンドラーは、次のタスクを実行します。

    - <xref:System.Windows.UIElement.Drop>イベントが既に処理されているかどうかを確認します。 たとえば、 <xref:System.Windows.UIElement.Drop>イベントを処理する別の円に円がドロップされた場合、その円を含むパネルにもハンドルを表示させたくありません。

    - イベントが処理されない場合は、Ctrl キーが押されたかどうかを確認します。 <xref:System.Windows.UIElement.Drop>

    - が発生し<xref:System.Windows.UIElement.Drop>たときに Ctrl キーを押すと、によって円コントロールのコピーが作成さ<xref:System.Windows.Controls.Panel.Children%2A>れ、の<xref:System.Windows.Controls.StackPanel>コレクションに追加されます。

    - **Ctrl**キーが押されていない場合、は、 <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Panel.Children%2A>親パネルのコレクションから、削除されたパネルのコレクションに円を移動します。

    - プロパティを設定して、 <xref:System.Windows.DragDrop.DoDragDrop%2A>移動またはコピー操作が実行されたかどうかをメソッドに通知します。 <xref:System.Windows.DragEventArgs.Effects%2A>

6. **F5** キーを押してアプリケーションをビルドし、実行します。

7. からテキスト`green`を選択します。<xref:System.Windows.Controls.TextBox>

8. 円コントロールの上にテキストをドラッグしてドロップします。

9. 左パネルから右パネルに円コントロールをドラッグしてドロップします。 左側のパネルの<xref:System.Windows.Controls.Panel.Children%2A>コレクションから円が削除され、右側のパネルの子コレクションに追加されます。

10. [円] コントロールをパネルからもう一方のパネルにドラッグし、 **Ctrl**キーを押しながらドロップします。 円がコピーされ、コピーが受信パネルの<xref:System.Windows.Controls.Panel.Children%2A>コレクションに追加されます。

     ![CTRL キーを押しながら円をドラッグする](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>関連項目

- [ドラッグ アンド ドロップの概要](drag-and-drop-overview.md)
