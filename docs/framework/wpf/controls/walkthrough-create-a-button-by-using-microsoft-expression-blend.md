---
title: 'チュートリアル: Microsoft Expression Blend を使用してボタンを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 1b4c775ea0680dcd8252a98c722dfe8f7e62548f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942498"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>チュートリアル: Microsoft Expression Blend を使用してボタンを作成する
このチュートリアルでは、Microsoft Expression Blend を使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]してカスタマイズされたボタンを作成する手順について説明します。  
  
> [!IMPORTANT]
> Microsoft Expression Blend は、実行[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]可能プログラムを作成するためにコンパイルされるを生成することによって機能します。 を[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]直接操作する場合は、Blend ではなく Visual Studio を使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 、同じアプリケーションを作成するもう1つのチュートリアルがあります。 詳細について[は、「XAML を使用したボタンの作成](walkthrough-create-a-button-by-using-xaml.md)」を参照してください。  
  
 次の図は、作成するカスタマイズされたボタンを示しています。  
  
 ![作成するカスタマイズされたボタン](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>図形をボタンに変換する  
 このチュートリアルの最初の部分では、カスタムボタンの外観を独自に作成します。 これを行うには、最初に四角形をボタンに変換します。 次に、ボタンのテンプレートに図形を追加して、より複雑な外観のボタンを作成します。 通常のボタンで開始してカスタマイズするのはなぜですか。 ボタンには必要のない組み込みの機能があるため、カスタムボタンの場合は、四角形から始める方が簡単です。  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Expression Blend で新しいプロジェクトを作成するには  
  
1. Expression Blend を開始します。 ( **[スタート]** をクリックし、 **[すべてのプログラム]** 、 **[microsoft expression]** の順にポイントし、 **[microsoft expression Blend]** をクリックします)。  
  
2. 必要に応じて、アプリケーションを最大化します。  
  
3. **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。  
  
4. **[標準アプリケーション (.exe)]** を選択します。  
  
5. プロジェクト`CustomButton`に名前を指定し、 **[OK]** をクリックします。  
  
 この時点で、空[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のプロジェクトがあります。 F5 キーを押してアプリケーションを実行できます。 ご想像のとおり、アプリケーションは空のウィンドウだけで構成されています。 次に、角丸四角形を作成し、ボタンに変換します。  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>四角形をボタンに変換するには  
  
1. **Window Background プロパティを black に設定します。** ウィンドウを選択し、[**プロパティ] タブ**をクリックし<xref:System.Windows.Controls.Control.Background%2A>て、 `Black`プロパティをに設定します。  
  
     ![ボタンの背景を黒に設定する方法](./media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2. **ウィンドウのボタンのサイズとほぼ同じ四角形を描画します。** 左側のツールパネルで [四角形] ツールを選択し、四角形をウィンドウにドラッグします。  
  
     ![四角形を描画する方法](./media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3. **四角形の角を丸めます。** 四角形のコントロールポイントをドラッグするか、プロパティ<xref:System.Windows.Shapes.Rectangle.RadiusX%2A>と<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>プロパティを直接設定します。 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> と<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>の値を20に設定します。  
  
     ![四角形の角を丸くする方法](./media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4. **四角形をボタンに変更します。** 四角形を選択します。 **[ツール]** メニューの [**作成] ボタン**をクリックします。  
  
     ![図形をボタンにする方法](./media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5. **スタイル/テンプレートのスコープを指定します。** 次のようなダイアログボックスが表示されます。  
  
     ![[スタイルリソースの作成] ダイアログボックス](./media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     **[リソース名 (キー)]** で、 **[すべてに適用]** を選択します。  これにより、結果のスタイルとボタンテンプレートが、ボタンであるすべてのオブジェクトに適用されます。 [**定義] で**、 **[アプリケーション]** を選択します。 これにより、結果のスタイルとボタンテンプレートにアプリケーション全体のスコープが設定されます。 これらの2つのボックスの値を設定すると、ボタンのスタイルとテンプレートはアプリケーション全体のすべてのボタンに適用され、アプリケーションで作成したボタンは既定でこのテンプレートを使用します。  
  
## <a name="edit-the-button-template"></a>ボタンテンプレートを編集する  
 これで、四角形がボタンに変更されました。 このセクションでは、ボタンのテンプレートを変更し、その外観をカスタマイズします。  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>ボタンテンプレートを編集してボタンの外観を変更するには  
  
1. **テンプレートビューの編集に進む:** ボタンの外観をさらにカスタマイズするには、ボタンテンプレートを編集する必要があります。 このテンプレートは、四角形をボタンに変換したときに作成されたものです。 ボタンテンプレートを編集するには、ボタンを右クリックし、[**コントロールパーツの編集] (テンプレート)** 、 **[テンプレートの編集]** の順に選択します。  
  
     ![テンプレートを編集する方法](./media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     テンプレートエディターで、ボタンが<xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.ContentPresenter>とに分割されていることを確認します。 は<xref:System.Windows.Controls.ContentPresenter> 、ボタン内にコンテンツを表示するために使用されます (たとえば、文字列 "button")。 四角形とは両方<xref:System.Windows.Controls.ContentPresenter>とも内<xref:System.Windows.Controls.Grid>にレイアウトされます。  
  
     ![四角形のプレゼンテーション内のコンポーネント](./media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2. **テンプレートコンポーネントの名前を変更します。** テンプレートインベントリ内の四角形を右クリックし、 <xref:System.Windows.Shapes.Rectangle>名前を "[四角形]" から "outerRectangle" に変更し、"[ContentPresenter]" を "myContentPresenter" に変更します。  
  
     ![テンプレートのコンポーネントの名前を変更する方法](./media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3. **(ドーナツのように) 内側に空になるように四角形を変更します。** **OuterRectangle**を選択し<xref:System.Windows.Shapes.Shape.Fill%2A> 、を "Transparent" <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>に、を5に設定します。  
  
     ![四角形を空にする方法](./media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     次に、 <xref:System.Windows.Shapes.Shape.Stroke%2A>を、テンプレートのすべての色に設定します。 これを行うには、 **[ストローク]** の横にある小さな白いボックスをクリックし、 **[customexpression]** を選択して、ダイアログボックスに「{TemplateBinding Background}」と入力します。  
  
     ![テンプレートの色を使用する方法を設定する方法](./media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4. **内部の四角形を作成します。** 次に、別の四角形を作成し ("innerRectangle" という名前を指定)、 **outerRectangle**の内部に対称的に配置します。 このような作業では、ズームして、編集領域のボタンのサイズを大きくすることをお勧めします。  
  
    > [!NOTE]
    > 四角形は、図の場合とは異なる場合があります (たとえば、角が丸くなる場合があります)。  
  
     ![別の四角形の中に四角形を作成する方法](./media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5. **ContentPresenter を一番上に移動します。** この時点で、テキスト "Button" が表示されなくなる可能性があります。 これが原因である場合、これは、 **Innerrectangle**が**myContentPresenter**の上にあるためです。 これを修正するには、 **myContentPresenter**を**innerrectangle**の下にドラッグします。 四角形と**myContentPresenter**の位置を変更して、次のようにします。  
  
    > [!NOTE]
    > または、 **myContentPresenter**を右クリックして **[Send Forward]** をクリックして、上に配置することもできます。  
  
     ![1 つのボタンを別のボタンの上に移動する方法](./media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6. **InnerRectangle の外観を変更します。** 、 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> 、<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>およびの値を20に<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>設定します。 さらに、カスタム式<xref:System.Windows.Shapes.Shape.Fill%2A> "{TemplateBinding background}" を使用してテンプレートの背景をに設定し、を<xref:System.Windows.Shapes.Shape.Stroke%2A> "transparent" に設定します。 <xref:System.Windows.Shapes.Shape.Fill%2A> **Innerrectangle**のおよびの設定は<xref:System.Windows.Shapes.Shape.Stroke%2A> 、 **outerRectangle**のとは逆の設定であることに注意してください。  
  
     ![四角形の外観を変更する方法](./media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7. **グラスレイヤーを上に追加します。** ボタンの外観をカスタマイズする最後の部分は、ガラスレイヤーを上部に追加することです。 このグラスレイヤーは、3番目の四角形で構成されています。 グラスではボタン全体が表示されるので、ガラスの四角形は**outerRectangle**のような大きさに似ています。 そのため、 **outerRectangle**のコピーを作成するだけで、四角形を作成できます。 **OuterRectangle**を強調表示し、Ctrl + C キーと Ctrl + V キーを使用してコピーを作成します。 この新しい四角形に "glassCube" という名前を指定します。  
  
8. **必要に応じて glassCube の位置を変更します。** **GlassCube**がボタン全体をカバーするように配置されていない場合は、その位置にドラッグします。  
  
9. **GlassCube は、outerRectangle とは少し異なる形で指定します。** **GlassCube**のプロパティを変更します。 まず、 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>プロパティとプロパティを10に、を 2に変更します。<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>  
  
     ![GlassCube の表示設定](./media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **GlassCube をガラスのように表示します。** を glassy <xref:System.Windows.Shapes.Shape.Fill%2A>に設定します。これは、不透明度が 75% の線形グラデーションを使用して、白と透明度が異なる6分の間隔で透明色を交互に交互に表示します。 次に、グラデーションの分岐点を設定する方法を示します。  
  
    - グラデーションの分岐点 1:白 (アルファ値は 75%)  
  
    - グラデーションの分岐点 2:透明  
  
    - グラデーションの分岐点 3:白 (アルファ値は 75%)  
  
    - グラデーションの分岐点 4:透明  
  
    - グラデーションの分岐点 5:白 (アルファ値は 75%)  
  
    - グラデーションの分岐点 6:透明  
  
     これにより、"波" グラスが作成されます。  
  
     ![グラスのような四角形](./media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **グラスレイヤーを非表示にします。** Glassy レイヤーがどのように見えるかを確認したので、[**プロパティ] パネル**の [**外観] ウィンドウ**に戻り、不透明度を 0% に設定して非表示にします。 前のセクションでは、プロパティトリガーとイベントを使用して、グラスレイヤーを表示および操作します。  
  
     ![グラス四角形を非表示にする方法](./media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>ボタンの動作をカスタマイズする  
 この時点では、テンプレートを編集してボタンの表示をカスタマイズしていますが、ボタンは通常のボタンとは異なります (たとえば、マウスオーバーでの外観の変更、フォーカスの受け取り、クリックなど)。次の2つの手順では、これらのような動作をカスタムボタンにビルドする方法を示します。 単純なプロパティトリガーから始めて、イベントトリガーとアニメーションを追加します。  
  
#### <a name="to-set-property-triggers"></a>プロパティトリガーを設定するには  
  
1. **新しいプロパティ トリガーを作成します。**  **GlassCube** 選択されていること、 **+ プロパティ** で、 **トリガー** パネル (次の手順を次の図を参照してください)。 これにより、既定のプロパティトリガーを持つプロパティトリガーが作成されます。  
  
2. **トリガーによって使用されるプロパティを次のように設定します。** プロパティをに<xref:System.Windows.UIElement.IsMouseOver%2A>変更します。 これにより、プロパティが<xref:System.Windows.UIElement.IsMouseOver%2A> `true`の場合 (ユーザーがマウスを使用してボタンをポイントしたとき)、プロパティトリガーがアクティブになります。  
  
     ![プロパティにトリガーを設定する方法](./media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3. **GlassCube の IsMouseOver トリガーの 100% の不透明度。** **トリガーの記録がオンになっ**ていることに注意してください (前の図を参照してください)。 つまり、記録中に**glassCube**のプロパティ値に加えた変更は、が<xref:System.Windows.UIElement.IsMouseOver%2A> `true`のときに行われるアクションになります。 記録中に、 <xref:System.Windows.UIElement.Opacity%2A> **glassCube**のを 100% に変更します。  
  
     ![ボタンの不透明度を設定する方法](./media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     これで、最初のプロパティトリガーが作成されました。 エディターの [**トリガー] パネル**に、変更され<xref:System.Windows.UIElement.Opacity%2A>たが 100% に記録されていることがわかります。  
  
     ![[トリガー] パネル](./media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     F5 キーを押してアプリケーションを実行し、マウスポインターをボタンの上または下に移動します。 ボタンをマウスでポイントするとグラスレイヤーが表示され、ポインターが離れると消えます。  
  
4. **IsMouseOver トリガーのストローク値の変更:** 他のアクションを<xref:System.Windows.UIElement.IsMouseOver%2A>トリガーに関連付けてみましょう。 記録が続行されたら、選択内容を**glassCube**から**outerRectangle**に切り替えます。 次に、 <xref:System.Windows.Shapes.Shape.Stroke%2A> **outerRectangle**のをカスタム式 "{dynamicresource {HighlightBrushKey}}" に設定します。 これにより<xref:System.Windows.Shapes.Shape.Stroke%2A> 、がボタンによって使用される一般的な強調表示色に設定されます。 F5 キーを押して、ボタンの上にマウスを置いたときの効果を確認します。  
  
     ![ストロークを強調表示色に設定する方法](./media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5. **IsMouseOver トリガーがぼやけたテキスト:** 1つ以上のアクションをプロパティトリガー <xref:System.Windows.UIElement.IsMouseOver%2A>に関連付けてみましょう。 ボタンの上にグラスが表示されているときに、ボタンの内容が少しぼやけて表示されるようにします。 これを行うには、 <xref:System.Windows.Media.Effects.BitmapEffect> <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**) にぼかしを適用します。  
  
     ![ボタンの内容をぼかす方法](./media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    > [**プロパティ] パネル**を検索<xref:System.Windows.Media.Effects.BitmapEffect>を開始する前の内容に戻すには、**検索ボックス**のテキストをクリアします。  
  
     この時点で、いくつかの関連するアクションを含むプロパティトリガーを使用して、マウスポインターがボタン領域に出入りするときの強調表示動作を作成しました。 ボタンのもう1つの一般的な動作は、フォーカスがあるときに強調表示されます (クリックされた後)。 このような動作を追加するには、 <xref:System.Windows.UIElement.IsFocused%2A>プロパティに対して別のプロパティトリガーを追加します。  
  
6. **IsFocused のプロパティトリガーを作成します。** と<xref:System.Windows.UIElement.IsMouseOver%2A>同じ手順 (このセクションの最初の手順を参照) を使用して、 <xref:System.Windows.UIElement.IsFocused%2A>プロパティに対して別のプロパティトリガーを作成します。 **トリガーの記録がオンになって**いる間に、次のアクションをトリガーに追加します。  
  
    - **glassCube**は、 <xref:System.Windows.UIElement.Opacity%2A> 100% のを取得します。  
  
    - **outerRectangle**は、 <xref:System.Windows.Shapes.Shape.Stroke%2A> "{dynamicresource {x:Static systemcolors}}" というカスタム式の値を取得します。  
  
 このチュートリアルの最後の手順として、アニメーションをボタンに追加します。 これらのアニメーションは、イベント、イベント、 <xref:System.Windows.UIElement.MouseEnter> <xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントによってトリガーされます。  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>イベントトリガーとアニメーションを使用して対話機能を追加するには  
  
1. **MouseEnter イベントトリガーを作成します。** 新しいイベントトリガーを追加し、 <xref:System.Windows.UIElement.MouseEnter>トリガーで使用するイベントとしてを選択します。  
  
     ![MouseEnter イベントトリガーを作成する方法](./media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2. **アニメーションタイムラインを作成します。** 次に、アニメーションタイムラインを<xref:System.Windows.UIElement.MouseEnter>イベントに関連付けます。  
  
     ![イベントにアニメーションタイムラインを追加する方法](./media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     **[OK]** をクリックして新しいタイムラインを作成すると、[タイムライン **] パネル**が表示され、[タイムラインの記録がオンになっています] がデザインパネルに表示されます。 これは、タイムラインでプロパティの変更の記録を開始できることを意味します (プロパティの変更をアニメーション化します)。  
  
    > [!NOTE]
    > 画面を表示するには、ウィンドウやパネルのサイズを変更する必要がある場合があります。  
  
     ![[タイムライン] パネル](./media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3. **キーフレームを作成します。** アニメーションを作成するには、アニメーション化するオブジェクトを選択し、タイムライン上に複数のキーフレームを作成します。これらのキーフレームについては、アニメーションで補間するプロパティ値を設定します。 次の図は、キーフレームを作成する手順を示しています。  
  
     ![キーフレームを作成する方法](./media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4. **このキーフレームで glassCube を圧縮します。** 2番目のキーフレームを選択した状態で、**サイズ変換**を使用して、 **glassCube**のサイズを完全なサイズの 90% に縮小します。  
  
     ![ボタンのサイズを縮小する方法](./media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     F5 キーを押してアプリケーションを実行します。 マウスポインターをボタンの上に移動します。 グラスレイヤーがボタンの上に縮小されることに注意してください。  
  
5. **別のイベントトリガーを作成し、別のアニメーションを関連付けます。** もう1つアニメーションを追加してみましょう。 前のイベントトリガーアニメーションの作成に使用したものと同様の手順を使用します。  
  
    1. <xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを使用して、新しいイベントトリガーを作成します。  
  
    2. 新しいタイムラインを<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントに関連付けます。  
  
     ![新しいタイムラインを作成する方法](./media/custom-button-blend-clickeventtrigger1.png "custom_button_blend_ClickEventTrigger1")  
  
    1. このタイムラインでは、2つのキーフレームを作成します。1つは0.0 秒、2番目は0.3 秒です。  
  
    2. キーフレームが0.3 秒で強調表示されている状態で、**回転変換の角度**を360度に設定します。  
  
     ![回転変換を作成する方法](./media/custom-button-blend-rotatetransform.gif "custom_button_blend_RotateTransform")  
  
    1. F5 キーを押してアプリケーションを実行します。 ボタンをクリックします。 グラスレイヤーが回転していることに注意してください。  
  
## <a name="conclusion"></a>まとめ  
 カスタマイズしたボタンを完了しました。 これを行うには、アプリケーションのすべてのボタンに適用されたボタンテンプレートを使用します。 テンプレート編集モードをそのままにした場合 (次の図を参照してください)、さらにボタンを作成すると、既定のボタンのようにではなく、カスタムボタンのような外観と動作が表示されます。  
  
 ![カスタムボタンテンプレート](./media/custom-button-blend-scopeup.gif "custom_button_blend_ScopeUp")  
  
 ![同じテンプレートを使用する複数のボタン](./media/custom-button-blend-createmultiplebuttons.png "custom_button_blend_CreateMultipleButtons")  
  
 F5 キーを押してアプリケーションを実行します。 ボタンをクリックして、すべての動作が同じであることを確認します。  
  
 テンプレートをカスタマイズしている間は、 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Shape.Stroke%2A> **innerrectangle**のプロパティとプロパティ**outerRectangle**をテンプレートの背景 ({TemplateBinding background}) に設定します。 このため、個々のボタンの背景色を設定すると、設定した背景がそれぞれのプロパティに使用されます。 今すぐ背景を変更してみてください。 次の図では、さまざまなグラデーションが使用されています。 したがって、テンプレートはボタンのようなコントロールを全体的にカスタマイズするのに役立ちますが、テンプレートを持つコントロールは、互いに異なる外観に変更される可能性があります。  
  
 ![外観のような同じテンプレートを持つボタン](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")  
  
 結論として、ボタンテンプレートをカスタマイズするプロセスでは、Microsoft Expression Blend で次の操作を行う方法を学習しました。  
  
- コントロールの外観をカスタマイズします。  
  
- プロパティトリガーを設定します。 プロパティトリガーは、コントロールだけでなく、ほとんどのオブジェクトで使用できるため、非常に便利です。  
  
- イベントトリガーを設定します。 イベントトリガーは、コントロールだけでなく、ほとんどのオブジェクトで使用できるため、非常に便利です。  
  
- アニメーションを作成します。  
  
- その他: グラデーションを作成し、BitmapEffects を追加し、変換を使用して、オブジェクトの基本プロパティを設定します。  
  
## <a name="see-also"></a>関連項目

- [XAML を使用したボタンの作成](walkthrough-create-a-button-by-using-xaml.md)
- [スタイルとテンプレート](styling-and-templating.md)
- [アニメーションの概要](../graphics-multimedia/animation-overview.md)
- [純色およびグラデーションによる塗りつぶしの概要](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [ビットマップ効果の概要](../graphics-multimedia/bitmap-effects-overview.md)
