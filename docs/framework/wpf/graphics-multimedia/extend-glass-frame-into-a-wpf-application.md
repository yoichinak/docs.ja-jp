---
title: WPF アプリケーションへのグラス フレームの拡張
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
ms.openlocfilehash: 8da1f49bf5b7d3daf6319906fb49390c008d209c
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412215"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>WPF アプリケーションへのグラス フレームの拡張

このトピックでは、拡張する方法を示します、 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] Windows Presentation Foundation (WPF) アプリケーションのクライアント領域にグラス フレーム。

> [!NOTE]
> この例は、グラスが有効なデスクトップ ウィンドウ マネージャー (DWM) を実行している [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] コンピューターでしか動作しません。 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Home Basic エディションは、透明グラス効果をサポートしていません。 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] の他のエディションで通常透明グラス効果がレンダリングされる領域は、不透明でレンダリングされます。

## <a name="example"></a>例

次の図に、アドレス バーの Internet Explorer 7 の拡張されたグラス フレームを示しています。

![スクリーン ショットのグラス フレームが IE7 のアドレス バーの背後に拡張します。](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションにグラス フレームを拡張するには、アンマネージ [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] へのアクセスが必要です。 次のコード例では、クライアント領域にフレームを拡張するために必要な 2 つの [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] のプラットフォーム呼び出し (pinvoke) を行っています。 これらの各 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] は、**NonClientRegionAPI** という名前のクラスで宣言されています。

```csharp
[StructLayout(LayoutKind.Sequential)]
public struct MARGINS
{
    public int cxLeftWidth;      // width of left border that retains its size
    public int cxRightWidth;     // width of right border that retains its size
    public int cyTopHeight;      // height of top border that retains its size
    public int cyBottomHeight;   // height of bottom border that retains its size
};

[DllImport("DwmApi.dll")]
public static extern int DwmExtendFrameIntoClientArea(
    IntPtr hwnd,
    ref MARGINS pMarInset);
```

```vb
<StructLayout(LayoutKind.Sequential)>
Public Structure MARGINS
    Public cxLeftWidth As Integer ' width of left border that retains its size
    Public cxRightWidth As Integer ' width of right border that retains its size
    Public cyTopHeight As Integer ' height of top border that retains its size
    Public cyBottomHeight As Integer ' height of bottom border that retains its size
End Structure

<DllImport("DwmApi.dll")>
Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer
End Function
```

[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) は、クライアント領域にフレームを拡張する DWM 関数です。 ウィンドウ ハンドルと [MARGINS](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) 構造体の 2 つのパラメーターを受け取ります。 [MARGINS](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) は、フレームがクライアント領域に余分に拡張する量を DWM に通知するために使われます。

## <a name="example"></a>例

[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) 関数を使うには、ウィンドウ ハンドルを取得する必要があります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]から、ウィンドウ ハンドルを取得できます、<xref:System.Windows.Interop.HwndSource.Handle%2A>のプロパティ、<xref:System.Windows.Interop.HwndSource>します。 次の例では、クライアント領域にフレームを拡張で、<xref:System.Windows.FrameworkElement.Loaded>ウィンドウのイベント。

```csharp
void OnLoaded(object sender, RoutedEventArgs e)
{
   try
   {
      // Obtain the window handle for WPF application
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);

      // Get System Dpi
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);
      float DesktopDpiX = desktop.DpiX;
      float DesktopDpiY = desktop.DpiY;

      // Set Margins
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();

      // Extend glass frame into client area
      // Note that the default desktop Dpi is 96dpi. The  margins are
      // adjusted for the system Dpi.
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));

      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);
      //
      if (hr < 0)
      {
         //DwmExtendFrameIntoClientArea Failed
      }
   }
   // If not Vista, paint background white.
   catch (DllNotFoundException)
   {
      Application.Current.MainWindow.Background = Brushes.White;
   }
}
```

## <a name="example"></a>例

次の例では、クライアント領域にフレームが拡張される簡単なウィンドウを示します。 フレームは、2 つを含む上罫線の背後にある<xref:System.Windows.Controls.TextBox>オブジェクト。

```xaml
<Window x:Class="SDKSample.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Extended Glass in WPF" Height="300" Width="400"
    Loaded="OnLoaded" Background="Transparent"
    >
  <Grid ShowGridLines="True">
    <DockPanel Name="mainDock">
      <!-- The border is used to compute the rendered height with margins.
           topBar contents will be displayed on the extended glass frame.-->
      <Border Name="topBar" DockPanel.Dock="Top" >
        <Grid Name="grid">
          <Grid.ColumnDefinitions>
            <ColumnDefinition MinWidth="100" Width="*"/>
            <ColumnDefinition Width="Auto"/>
          </Grid.ColumnDefinitions>
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>
        </Grid>
      </Border>
      <Grid DockPanel.Dock="Top" >
        <Grid.ColumnDefinitions>
          <ColumnDefinition/>
        </Grid.ColumnDefinitions>
        <TextBox Grid.Column="0" AcceptsReturn="True"/>
      </Grid>
    </DockPanel>
  </Grid>
</Window>
```

次の図に拡張されたグラス フレームを[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーション。

![WPF アプリケーションに拡張されたグラス フレームを示すスクリーン ショット。](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a>関連項目

- [デスクトップ ウィンドウ マネージャーの概要](/windows/desktop/dwm/dwm-overview)
- [デスクトップ ウィンドウ マネージャーのぼかしの概要](/windows/desktop/dwm/blur-ovw)
- [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
