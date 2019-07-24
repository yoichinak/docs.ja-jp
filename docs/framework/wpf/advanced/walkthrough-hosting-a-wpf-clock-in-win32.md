---
title: 'チュートリアル: Win32 での WPF クロックのホスト'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 98e48060bbb82764e1e541797c666ca33f247c39
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400482"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>チュートリアル: Win32 での WPF クロックのホスト

アプリケーション内[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]に配置するに<xref:System.Windows.Interop.HwndSource>は、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用します。これにより、コンテンツを含む HWND が提供されます。 最初にを作成<xref:System.Windows.Interop.HwndSource>し、CreateWindow のようなパラメーターを指定します。 <xref:System.Windows.Interop.HwndSource> 次[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に、その中に必要なコンテンツについて説明します。 最後に、から HWND <xref:System.Windows.Interop.HwndSource>を取得します。 このチュートリアルでは、[オペレーティングシステム[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] **日付と時刻のプロパティ**] ダイアログを再実装する、混在するアプリケーションを作成する方法について説明します。

## <a name="prerequisites"></a>必須コンポーネント

「 [WPF と Win32 の相互運用」を](wpf-and-win32-interoperation.md)参照してください。

## <a name="how-to-use-this-tutorial"></a>このチュートリアルの使用方法

このチュートリアルでは、相互運用アプリケーションを生成するための重要な手順について説明します。 このチュートリアルは、サンプルの[Win32 クロック相互運用のサンプル](https://go.microsoft.com/fwlink/?LinkID=160051)によって支えられていますが、そのサンプルは終了製品を反映しています。 このチュートリアルでは、自分が所有している既存[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]のプロジェクト (おそらく既存のプロジェクト) で作業を開始していて、ホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]されているをアプリケーションに追加している場合と同様の手順について説明します。 [Win32 クロック相互運用のサンプル](https://go.microsoft.com/fwlink/?LinkID=160051)を使用して、終了製品を比較することができます。

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Win32 内の Windows Presentation Framework のチュートリアル (System.windows.interop.hwndsource>)

次の図は、このチュートリアルの目的の最終製品を示しています。

![[日付と時刻のプロパティ] ダイアログボックスを表示するスクリーンショット。](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

このダイアログを再作成するにはC++ 、Visual Studio で Win32 プロジェクトを作成し、ダイアログエディターを使用して次のものを作成します。

![[再作成された日付と時刻のプロパティ] ダイアログボックス](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(を使用するためにを[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]使用する<xref:System.Windows.Interop.HwndSource>必要はありませんが、プログラムC++の作成[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]にを使用する必要はありませんが、これは非常に一般的な方法であり、ステップごとのチュートリアルの説明に適しています)。

ダイアログに時計を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]配置するには、5つの特定の手順を実行する必要があります。

1. でプロジェクト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]の設定を変更することにより、プロジェクトで[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]マネージコード ( **/clr**) を呼び出すことができるようにします。

2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を<xref:System.Windows.Controls.Page>別の DLL に作成します。

3. を内[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>に配置します。 <xref:System.Windows.Interop.HwndSource>

4. プロパティを使用して<xref:System.Windows.Controls.Page> 、そのの HWND を取得します。 <xref:System.Windows.Interop.HwndSource.Handle%2A>

5. より[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 大きな[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーション内で HWND を配置する場所を決定するために使用します

## <a name="clr"></a>/clr

最初の手順では、アン[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]マネージプロジェクトをマネージコードを呼び出すことができるようにします。 /Clr コンパイラオプションを使用します。このオプションは、使用する必要な Dll にリンクし、で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用するための Main メソッドを調整します。

C++プロジェクト内でマネージコードを使用できるようにするには、次のようにします。Win32clock プロジェクトを右クリックし、 **[プロパティ]** を選択します。 **全般** プロパティページ (既定) で、共通言語ランタイムサポート `/clr`をに変更します。

次に、に必要な Dll へ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の参照を追加します。プレゼンテーションのコア .dll、プレゼンテーションフレームワーク .dll、.dll、WindowsBase .dll、Uiautomationprovider.dll、および Uiautomationtypes.dll があります。 (以下の手順は、オペレーティングシステムが C: ドライブにインストールされていることを前提としています)。

1. Win32clock project を右クリックし、**参照** をクリックして、そのダイアログ内でを選択します。

2. Win32clock プロジェクト を右クリックし、**参照** を選択します。

3. **新しい参照の追加** をクリックし、参照 タブをクリックして、「C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll」と入力し、OK をクリックします。

4. プレゼンテーションフレームワーク .dll に対して繰り返します。C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.

5. WindowsBase .dll に対してこの手順を繰り返します。C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.

6. Uiautomationtypes.dll に対してこの手順を繰り返します。C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.

7. Uiautomationprovider.dll に対してこの手順を繰り返します。C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.

8. **新しい参照の追加** をクリックし、.dll を選択して、 **OK**をクリックします。

9. **[OK]** をクリックして、参照を追加するための Win32clock プロパティページを終了します。

 最後に、を`STAThreadAttribute`と共`_tWinMain` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に使用するために、をメソッドに追加します。

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

この属性は、初期化[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]時に共通言語ランタイム (CLR) に通知します。これは、(および[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]) に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]必要なシングルスレッドアパートメントモデル (STA) を使用する必要があります。

## <a name="create-a-windows-presentation-framework-page"></a>Windows Presentation Framework ページを作成する

次に、を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>定義する DLL を作成します。 多くの場合、をスタンドアロン[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション<xref:System.Windows.Controls.Page>として作成[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]し、その部分を記述してデバッグするのが最も簡単です。 完了したら、プロジェクトを右クリックし、**プロパティ** をクリックして、アプリケーションに移動し、出力の種類 を Windows クラスライブラリ に変更することにより、そのプロジェクトを DLL に変換できます。

Dll プロジェクトは、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プロジェクト (2 つのプロジェクトを含む1つのソリューション) と組み合わせることができます。ソリューションを右クリックし、 **[Add\Existing プロジェクト]** を選択します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

プロジェクトからその[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll を使用するには、参照を追加する必要があります。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]

1. Win32clock プロジェクト を右クリックし、**参照** を選択します。

2. **[新しい参照の追加]** をクリックします。

3. **[プロジェクト]** タブをクリックします。WPFClock を選択し、[OK] をクリックします。

4. **[OK]** をクリックして、参照を追加するための Win32clock プロパティページを終了します。

## <a name="hwndsource"></a>System.windows.interop.hwndsource>

次に、を<xref:System.Windows.Interop.HwndSource>使用して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、HWND の<xref:System.Windows.Controls.Page>ように表示します。 次のコードブロックをC++ファイルに追加します。

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;

    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
        HwndSource^ source = gcnew HwndSource(
            0, // class style
            WS_VISIBLE | WS_CHILD, // style
            0, // exstyle
            x, y, width, height,
            "hi", // NAME
            IntPtr(parent)        // parent window
            );

        UIElement^ page = gcnew WPFClock::Clock();
        source->RootVisual = page;
        return (HWND) source->Handle.ToPointer();
    }
}
}
```

 これは、何らかの説明を使用できる長いコードです。 最初の部分はさまざまな句であり、すべての呼び出しを完全に修飾する必要がありません。

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 次に、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツを作成して<xref:System.Windows.Interop.HwndSource>周囲に配置し、HWND を返す関数を定義します。

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

まず、パラメーターが<xref:System.Windows.Interop.HwndSource>CreateWindow に似ているを作成します。

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

次に、その[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンストラクターを呼び出してコンテンツクラスを作成します。

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

次に、 <xref:System.Windows.Interop.HwndSource>ページをに接続します。

```cpp
source->RootVisual = page;
```

 最後の行で、の HWND <xref:System.Windows.Interop.HwndSource>を返します。

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Hwnd の配置

これで、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時計を含む hwnd が作成されたので、この hwnd を[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ダイアログ内に配置する必要があります。 HWND をどこに配置するかがわかっていれば、先ほど定義した`GetHwnd`関数にそのサイズと場所を渡すだけです。 ただし、リソースファイルを使用してダイアログを定義したので、Hwnd がどこに配置されているかを正確に確認することはできません。 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]ダイアログエディターを使用して、時計の[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]移動先 ("ここに時計を挿入する") に静的コントロールを配置し、それを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用して時計を配置できます。

WM_INITDIALOG を処理する場合は、 `GetDlgItem`を使用して、プレースホルダー STATIC の HWND を取得します。

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

次に、そのプレースホルダーのサイズと位置を計算し、その場所に時計[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を配置できるようにします。

RECT 四角形;

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

次に、プレースホルダーを静的に非表示にします。

```cpp
ShowWindow(placeholder, SW_HIDE);
```

次のよう[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に、その場所に時計 HWND を作成します。

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

このチュートリアルをおもしろいものにし、実際[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の時計を生成するには、この時点で時計コントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]作成する必要があります。 多くの場合、コードビハインドでいくつかのイベントハンドラーを使用するだけで、マークアップでこれを行うことができます。 このチュートリアルは相互運用に関するものであり、コントロールの設計に関する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ものではないため、この時計の完全なコードはコードブロックとして提供されています。これは、ビルドのための個別の指示や各部分の意味を持ちません。 このコードを自由に試して、コントロールの外観や外観を変更してください。

マークアップは次のとおりです。

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

次に、関連する分離コードを示します。

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

最終的な結果は次のようになります。

![[最終結果の日付と時刻のプロパティ] ダイアログボックス](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

このスクリーンショットを生成したコードと結果を比較するには、「 [Win32 Clock 相互運用のサンプル](https://go.microsoft.com/fwlink/?LinkID=160051)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.HwndSource>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [Win32 クロック相互運用のサンプル](https://go.microsoft.com/fwlink/?LinkID=160051)
