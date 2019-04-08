---
title: 'チュートリアル: XAML を使用したボタンの作成'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: c092ad49f40257467245a07a6e4b9849822e1835
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076563"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>チュートリアル: XAML を使用したボタンの作成
このチュートリアルでは、Windows Presentation Foundation (WPF) アプリケーションで使用するためのアニメーションのボタンを作成する方法について説明します。 このチュートリアルでは、スタイルとテンプレートを使用して、コードの再利用し、ボタンの宣言からボタンのロジックの分離を許可するカスタマイズされたボタンのリソースを作成します。 このチュートリアルが完全に記述された[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。  
  
> [!IMPORTANT]
>  このチュートリアルで入力またはコピーして貼り付けることによって、アプリケーションを作成するための手順を説明する[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]に Microsoft Visual Studio。 デザイン ツール (Microsoft Expression Blend) を使用して、参照してください、同じアプリケーションを作成する方法を学習したい場合[Microsoft Expression Blend を使用してボタンを作成する](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)します。  
  
 次の図は、完成したボタンを示しています。  
  
 ![XAML を使用して作成されたカスタム ボタン](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>基本的なボタンを作成します。  
 新しいプロジェクトを作成し、ボタンをいくつかのウィンドウに追加してみましょう。  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>新しい WPF プロジェクトを作成し、ウィンドウにボタンを追加するには  
  
1.  Visual Studio を起動します。  
  
2.  **新しい WPF プロジェクトを作成します。** **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。 検索、 **Windows アプリケーション (WPF)** テンプレートとプロジェクト"AnimatedButton"の名前。 これにより、アプリケーションのスケルトンが作成されます。  
  
3.  **基本的な既定のボタンを追加します。** このチュートリアルで必要なすべてのファイルは、テンプレートによって提供されます。 ダブルクリックして、ソリューション エクスプ ローラーで、Window1.xaml ファイルを開きます。 既定では、 <xref:System.Windows.Controls.Grid> Window1.xaml 内の要素。 削除、<xref:System.Windows.Controls.Grid>要素をいくつかのボタンを追加して、 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 」と入力またはコピーして貼り付けることで Window1.xaml を強調表示されている次のコード ページ。  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>  
    </Window>  
    ```  
  
     F5 キーを押してアプリケーションを実行次の図のようなボタンのセットが表示されます。  
  
     ![3 つの基本的なボタン](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     基本的なボタンを作成するには、Window1.xaml ファイルの操作が完了したら。 このチュートリアルの残りの部分は、スタイルとボタンのテンプレートを定義する、app.xaml ファイルについて説明します。  
  
## <a name="set-basic-properties"></a>基本的なプロパティを設定します。  
 次に、ボタンの外観とレイアウトを制御するこれらのボタンをいくつかのプロパティを設定してみましょう。 ボタンのプロパティを個別に設定するのではなく、アプリケーション全体のボタンのプロパティを定義するのにリソースを使用します。 アプリケーション リソースは外部に概念的に似ています[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]Web ページです。 ただし、リソースはよりもはるかに強力な[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]、このチュートリアルの最後で表示されます。 リソースの詳細については、次を参照してください。 [XAML リソース](../advanced/xaml-resources.md)します。  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>スタイルを使用して、ボタンの基本プロパティを設定するには  
  
1.  **Application.Resources ブロックを定義します。** App.xaml を開きがない場合は、次の強調表示されたマークアップを追加します。  
  
    ```xaml  
    <Application x:Class="AnimatedButton.App"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      StartupUri="Window1.xaml"  
      >  
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>  
    </Application>  
    ```  
  
     リソースのスコープは、定義したリソースによって決定されます。 内のリソースを定義する`Application.Resources`app.xaml ファイル、アプリケーションで任意の場所から使用するリソースを使用できます。 詳細については、リソースのスコープを定義するを参照してください。 [XAML リソース](../advanced/xaml-resources.md)します。  
  
2.  **スタイルを作成し、基本的なプロパティ値を定義します。** 次のマークアップを追加、`Application.Resources`ブロックします。 このマークアップを作成、<xref:System.Windows.Style>設定、アプリケーションのすべてのボタンに適用する、<xref:System.Windows.FrameworkElement.Width%2A>を 90 にボタンの<xref:System.Windows.FrameworkElement.Margin%2A>10。  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A>プロパティは、型のすべてのオブジェクトにスタイルが適用されることを指定します<xref:System.Windows.Controls.Button>します。 各<xref:System.Windows.Setter>の別のプロパティ値を設定、<xref:System.Windows.Style>します。 そのため、この時点で、アプリケーション内のすべてのボタンが幅 90、余白は 10 です。  アプリケーションの実行に f5 キーを押すと、次のウィンドウが表示されます。  
  
     ![幅 90、余白 10 のボタン](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     さらに多くのさまざまなオブジェクトが対象となるを微調整する方法を含む、複合プロパティの値を指定しても入力としてスタイルを使用して、その他のスタイルのスタイルで行えるがあります。 詳しくは、「 [スタイルとテンプレート](styling-and-templating.md)」をご覧ください。  
  
3.  **リソースへのスタイル プロパティの値を設定します。** リソースには、一般的に定義されるオブジェクトと値を再利用する簡単な方法が有効にします。 リソースを使用して、コードをモジュール性の高い複雑な値を定義すると特に便利です。 App.xaml には、次の強調表示されたマークアップを追加します。  
  
    ```xaml  
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
    </Application.Resources>  
    ```  
  
     すぐ下、`Application.Resources`ブロック"GrayBlueGradientBrush"という名前のリソースを作成します。 このリソースは、水平方向のグラデーションを定義します。 このリソースをどこからでもプロパティの値として使用できますのボタン スタイル setter 内など、アプリケーションで、<xref:System.Windows.Controls.Control.Background%2A>プロパティ。 ここで、すべてのボタンがある、<xref:System.Windows.Controls.Control.Background%2A>このグラデーションのプロパティの値。  
  
     F5 キーを押してアプリケーションを実行します。 次のようになります。  
  
     ![グラデーション背景を持つボタン](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>ボタンの外観を定義するテンプレートを作成します。  
 このセクションでは、ボタンの外観 (presentation) をカスタマイズするテンプレートを作成します。 ボタンのプレゼンテーションは、ボタンの外観を一意に四角形とその他のコンポーネントを含むいくつかのオブジェクトの構成されます。  
  
 ここまでは、アプリケーションのボタンの外観の制御は、ボタンのプロパティの変更に制限されていましたが。 ボタンの外観をより大きく変更する場合は? テンプレートには、オブジェクトのプレゼンテーションに強力な制御が有効にします。 テンプレートは、スタイル内で使用できる、ため (このチュートリアルでは、ボタン) では、スタイルが適用されるすべてのオブジェクトにテンプレートを適用できます。  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>テンプレートを使用して、ボタンの外観を定義するには  
  
1.  **テンプレートを設定します。** コントロールなどのため、<xref:System.Windows.Controls.Button>が、<xref:System.Windows.Controls.Control.Template%2A>プロパティで設定している他のプロパティ値と同様、テンプレート プロパティの値を定義できますを<xref:System.Windows.Style>を使用して、<xref:System.Windows.Setter>します。 次の強調表示されたマークアップをボタンのスタイルに追加します。  
  
    ```xaml
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"   
        StartPoint="0,0" EndPoint="1,1">  
        <GradientStop Color="DarkGray" Offset="0" />  
        <GradientStop Color="#CCCCFF" Offset="0.5" />  
        <GradientStop Color="DarkGray" Offset="1" />  
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>  
      </Style>  
    </Application.Resources>  
    ```  
  
2.  **ボタンのプレゼンテーションを変更するには。** この時点では、テンプレートを定義する必要があります。 次の強調表示されたマークアップを追加します。 このマークアップでは、2 つを指定します<xref:System.Windows.Shapes.Rectangle>角の丸いを持つ要素が続く、<xref:System.Windows.Controls.DockPanel>します。 <xref:System.Windows.Controls.DockPanel>されるホストに、<xref:System.Windows.Controls.ContentPresenter>ボタンの。 A<xref:System.Windows.Controls.ContentPresenter>ボタンのコンテンツを表示します。 このチュートリアルでは、コンテンツは、テキスト (「ボタン 1」、「ボタン 2」、「ボタン 3」) です。 すべてのテンプレートのコンポーネント (四角形と<xref:System.Windows.Controls.DockPanel>) 内のレイアウトは、<xref:System.Windows.Controls.Grid>します。  
  
    ```xaml  
    <Setter.Value>  
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     F5 キーを押してアプリケーションを実行します。 次のようになります。  
  
     ![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3.  **テンプレートには、グラス効果を追加します。** 次に、ガラスを追加します。 まずガラスのグラデーション効果を作成するいくつかのリソースを作成します。 これらグラデーション内のリソース任意の場所を追加、`Application.Resources`ブロック。  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />     
        <GradientStop Color="Transparent" Offset="0.4" />    
        <GradientStop Color="WhiteSmoke" Offset="0.5" />     
        <GradientStop Color="Transparent" Offset="0.75" />     
        <GradientStop Color="WhiteSmoke" Offset="0.9" />     
        <GradientStop Color="Transparent" Offset="1" />   
      </GradientStopCollection>   
      <LinearGradientBrush x:Key="MyGlassBrushResource"    
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     これらのリソースとして使用、<xref:System.Windows.Shapes.Shape.Fill%2A>に挿入する四角形の<xref:System.Windows.Controls.Grid>ボタン テンプレートの。 テンプレートには、次の強調表示されたマークアップを追加します。  
  
    ```xaml
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"  
          ClipToBounds="True">  
  
        <!-- Outer Rectangle with rounded corners. -->  
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
        <!-- Inner Rectangle with rounded corners. -->  
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"   
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />  
  
        <!-- Glass Rectangle -->     
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"       
          VerticalAlignment="Stretch"       
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"       
          Fill="{StaticResource MyGlassBrushResource}"       
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>         
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>       
          </Rectangle.Stroke>       
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->       
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>  
  
        <!-- Present Text of the button. -->  
        <DockPanel Name="myContentPresenterDockPanel">  
          <ContentPresenter x:Name="myContentPresenter" Margin="20"   
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
        </DockPanel>  
      </Grid>  
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     注意して、<xref:System.Windows.UIElement.Opacity%2A>四角形の`x:Name`"glassCube"のプロパティが 0 の場合、サンプルを実行するときに、一番上にオーバーレイ グラス四角形は表示されないようにします。 これは後でトリガーを追加のテンプレートをユーザーがボタンであるためにです。 ボタンの外観のように今すぐ変更することによって、ご覧、 <xref:System.Windows.UIElement.Opacity%2A> 1 およびアプリケーションを実行する値。 次の図を参照してください。 次の手順に進む前に変更、<xref:System.Windows.UIElement.Opacity%2A>を 0 に戻します。  
  
     ![XAML を使用して作成されたカスタム ボタン](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>ボタンの対話機能を作成します。  
 このセクションでは、プロパティ トリガーと、プロパティ値を変更し、ボタンの上にマウス ポインターを移動し、クリックしてなどのユーザー アクションへの応答でアニメーションを実行するイベント トリガーを作成します。  
  
 対話機能 (マウス、マウスのままをクリックし、およびなど) を追加する簡単な方法では、テンプレートまたはスタイル内のトリガーを定義します。 作成する、<xref:System.Windows.Trigger>などのプロパティの"condition"を定義します。ボタン<xref:System.Windows.UIElement.IsMouseOver%2A>プロパティの値が等しく`true`します。 トリガー条件が true のときに行われるセッター (アクション) を定義します。  
  
#### <a name="to-create-button-interactivity"></a>ボタンの対話機能を作成するには  
  
1.  **テンプレートのトリガーを追加します。** テンプレートには、強調表示されたマークアップを追加します。  
  
    ```xaml
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}"   
          Height="{TemplateBinding Height}" ClipToBounds="True">  
  
          <!-- Outer Rectangle with rounded corners. -->  
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
          <!-- Inner Rectangle with rounded corners. -->  
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch" Stroke="Transparent"   
            StrokeThickness="20"   
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"   
          />  
  
          <!-- Glass Rectangle -->  
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"  
            VerticalAlignment="Stretch"  
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"  
            Fill="{StaticResource MyGlassBrushResource}"  
            RenderTransformOrigin="0.5,0.5">  
            <Rectangle.Stroke>  
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">  
                <LinearGradientBrush.GradientStops>  
                  <GradientStop Offset="0.0" Color="LightBlue" />  
                  <GradientStop Offset="1.0" Color="Gray" />  
                </LinearGradientBrush.GradientStops>  
              </LinearGradientBrush>  
            </Rectangle.Stroke>  
  
            <!-- These transforms have no effect as they   
                 are declared here.   
                 The reason the transforms are included is to be targets   
                 for animation (see later). -->  
            <Rectangle.RenderTransform>  
              <TransformGroup>  
                <ScaleTransform />  
                <RotateTransform />  
              </TransformGroup>  
            </Rectangle.RenderTransform>  
  
              <!-- A BevelBitmapEffect is applied to give the button a   
                   "Beveled" look. -->  
            <Rectangle.BitmapEffect>  
              <BevelBitmapEffect />  
            </Rectangle.BitmapEffect>  
          </Rectangle>  
  
          <!-- Present Text of the button. -->  
          <DockPanel Name="myContentPresenterDockPanel">  
            <ContentPresenter x:Name="myContentPresenter" Margin="20"   
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
          </DockPanel>  
        </Grid>  
  
        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
2.  **プロパティ トリガーを追加します。** 強調表示されたマークアップを追加、`ControlTemplate.Triggers`ブロック。  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     F5 キーを押してアプリケーションを実行し、ボタンの上にマウス ポインターを実行すると、影響を確認します。  
  
3.  **フォーカスのトリガーを追加します。** 次に、ボタンに (たとえば、ユーザーがクリックした後) にフォーカスがあるときに、ケースを処理するいくつかのような set アクセス操作子を追加します。  
  
    ```xaml  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->  
      <Trigger Property="IsMouseOver" Value="True">  
  
        <!-- Below are three property settings that occur when the   
             condition is met (user mouses over button).  -->  
        <!-- Change the color of the outer rectangle when user          mouses over it. -->  
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
  
        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->  
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />  
  
        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->  
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">  
          <Setter.Value>  
            <BlurBitmapEffect Radius="1" />  
          </Setter.Value>  
        </Setter>  
      </Trigger>  
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>  
  
    </ControlTemplate.Triggers>  
    ```  
  
     F5 キーを押してアプリケーションを実行し、ボタンのいずれかをクリックします。 フォーカスをしているために、クリックした後、ボタンが強調表示されたままことに注意してください。 新しいボタンに別のボタンをクリックすると、最後の 1 つがそれを失ったときにフォーカスを取得します。  
  
4.  **アニメーションを追加**<xref:System.Windows.UIElement.MouseEnter> **と** <xref:System.Windows.UIElement.MouseLeave> **:** 次に、トリガーに一部のアニメーションを追加します。 任意の場所内の次のマークアップを追加、`ControlTemplate.Triggers`ブロックします。  
  
    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->  
    <EventTrigger RoutedEvent="Mouse.MouseEnter">  
      <EventTrigger.Actions>  
        <BeginStoryboard Name="mouseEnterBeginStoryboard">  
          <Storyboard>  
          <!-- This animation makes the glass rectangle shrink in the X direction. -->  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"  
              By="-0.1" Duration="0:0:0.5" />  
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->  
            <DoubleAnimation  
            Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"   
              By="-0.1" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    <EventTrigger RoutedEvent="Mouse.MouseLeave">  
      <EventTrigger.Actions>  
        <!-- Stopping the storyboard sets all animated properties back to default. -->  
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     グラス四角形には、マウス ポインターがボタン上に移動し、ポインターが離れたときに通常のサイズを返しますが縮小されます。  
  
     ポインターがボタンを超えた場合にトリガーされる 2 つのアニメーションがある (<xref:System.Windows.UIElement.MouseEnter>イベントが発生します)。 これらのアニメーションは、X と Y 軸に沿ったグラス四角形を縮小します。 プロパティに注目してください、<xref:System.Windows.Media.Animation.DoubleAnimation>要素-<xref:System.Windows.Media.Animation.Timeline.Duration%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>します。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>を 0.5 秒、発生するアニメーションのことを指定します、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>ガラスが 10% に縮小ことを指定します。  
  
     2 番目のイベント トリガー (<xref:System.Windows.UIElement.MouseLeave>) 1 つ目を単純に停止します。 停止すると、 <xref:System.Windows.Media.Animation.Storyboard>、アニメーション化されたすべてのプロパティが既定値に戻ります。 そのため、ユーザーがポインター ボタンから離れると、ボタンに戻りますがマウス ポインターがボタンの上に移動する前にする方法。 アニメーションの詳細については、次を参照してください。[アニメーションの概要](../graphics-multimedia/animation-overview.md)します。  
  
5.  **ボタンがクリックされたときのアニメーションを追加します。** 最後の手順では、ユーザーがボタンをクリックしたときにトリガーを追加します。 任意の場所内の次のマークアップを追加、`ControlTemplate.Triggers`ブロック。  
  
    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->  
    <EventTrigger RoutedEvent="Button.Click">  
      <EventTrigger.Actions>  
        <BeginStoryboard>  
          <Storyboard>  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"   
              By="360" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     F5 キーを押して、アプリケーションを実行し、ボタンをクリックします。 ボタンをクリックすると、ガラスの四角形が回転します。  
  
## <a name="summary"></a>まとめ  
 このチュートリアルでは、次の演習を実行しました。  
  
-   対象となる、<xref:System.Windows.Style>オブジェクトの種類を (<xref:System.Windows.Controls.Button>)。  
  
-   アプリケーション全体を使用して、ボタンの基本プロパティを制御、<xref:System.Windows.Style>します。  
  
-   プロパティ値を使用するグラデーションなどのリソースを作成、 <xref:System.Windows.Style> set アクセス操作子。  
  
-   アプリケーション全体のボタンの外観をカスタマイズするには、ボタンにテンプレートを適用します。  
  
-   ユーザー操作に応じてボタンの動作をカスタマイズ (など<xref:System.Windows.UIElement.MouseEnter>、<xref:System.Windows.UIElement.MouseLeave>と<xref:System.Windows.Controls.Primitives.ButtonBase.Click>) アニメーション効果が含まれています。  
  
## <a name="see-also"></a>関連項目

- [Microsoft Expression Blend を使用してボタンを作成する](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [スタイルとテンプレート](styling-and-templating.md)
- [アニメーションの概要](../graphics-multimedia/animation-overview.md)
- [純色およびグラデーションによる塗りつぶしの概要](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [ビットマップ効果の概要](../graphics-multimedia/bitmap-effects-overview.md)
