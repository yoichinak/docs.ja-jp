---
title: 'チュートリアル: Win32 での WPF クロックのホスト'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 4001c34f6673e036bdbf731baed782c6dc0a16b0
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63808065"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>チュートリアル: Win32 での WPF クロックのホスト

配置する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーションに、<xref:System.Windows.Interop.HwndSource>を含む HWND を提供する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。 最初に作成、 <xref:System.Windows.Interop.HwndSource>CreateWindow のようなパラメーターを指定します。 わかり、<xref:System.Windows.Interop.HwndSource>について、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内するコンテンツ。 最後に、out の HWND を取得する、<xref:System.Windows.Interop.HwndSource>します。 このチュートリアルは、混合を作成する方法を示しています。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]オペレーティング システムを reimplements アプリケーション**日付と時刻のプロパティ**ダイアログ。

## <a name="prerequisites"></a>必須コンポーネント

参照してください[WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)します。

## <a name="how-to-use-this-tutorial"></a>このチュートリアルを使用する方法

このチュートリアルは相互運用アプリケーションの作成の重要な手順に重点を置いて説明します。 このチュートリアルはサンプルについては、によって支えられて[Win32 クロックの相互運用性サンプル](https://go.microsoft.com/fwlink/?LinkID=160051)が、そのサンプルは、最終的な製品の反射します。 既存の開始された場合、このチュートリアル手順について説明[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]独自のプロジェクトや既存のプロジェクトなどをホストされた追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションにします。 最終的な製品を比較する[Win32 クロックの相互運用性サンプル](https://go.microsoft.com/fwlink/?LinkID=160051)します。

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Win32 内部の Windows Presentation Framework のチュートリアル (HwndSource)

次の図は、このチュートリアルの目的の最終製品を示します。

![日付と時刻のプロパティ ダイアログ ボックスのスクリーン ショット。](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

このダイアログ ボックスを作成して再作成できます、 C++ Win32 プロジェクトを Visual Studio、およびダイアログ エディターを使用して、次を作成します。

![再作成された日付と時刻のプロパティ ダイアログ ボックス](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(を使用する必要はありません[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]を使用する<xref:System.Windows.Interop.HwndSource>、C++ を使用して記述する必要はありません[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]、これを行う非常に典型的な方法であり、プログラムが、このステップ チュートリアルについてにも適しています)。

配置するには 5 つの特定のサブ手順を実行する必要がある、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  ダイアログにクロックします。

1. 有効にする、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]マネージ コードを呼び出すためのプロジェクト (**/clr**) プロジェクトの設定を変更することで[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]します。

2. 作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>個別の DLL にします。

3. 追加する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>内で、<xref:System.Windows.Interop.HwndSource>します。

4. そのため、HWND を取得<xref:System.Windows.Controls.Page>を使用して、<xref:System.Windows.Interop.HwndSource.Handle%2A>プロパティ。

5. 使用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]内で、大規模な HWND を配置する場所を決定する[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーション

## <a name="clr"></a>/clr

この管理対象外にするには、まず[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プロジェクトを呼び出すことができる 1 つにマネージ コード。 Main メソッドで使用するために調整し、使用するために必要な Dll へのリンクは、/clr コンパイラ オプションを使用する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。

C++ プロジェクト内のマネージ コードの使用を有効にします。Win32clock プロジェクトを右クリックし、選択**プロパティ**します。 **全般**プロパティ ページ (既定)、変更を共通言語ランタイム サポート`/clr`します。

次に、必要な Dll への参照を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:Presentationcore.dll 内、PresentationFramework.dll、System.dll、WindowsBase.dll、UIAutomationProvider.dll および UIAutomationTypes.dll します。 (次の手順と仮定 c: ドライブに、オペレーティング システムがインストールされている。)

1. Win32clock プロジェクトを右クリックして**参照.**、およびそのダイアログ内。

2. Win32clock プロジェクトを右クリックして**参照.**.

3. クリックして**新しい参照の追加**[参照] タブをクリックして、C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll を入力して [ok] をクリックします。

4. PresentationFramework.dll を繰り返します。C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll します。

5. WindowsBase.dll を繰り返します。C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll します。

6. UIAutomationTypes.dll を繰り返します。C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.

7. UIAutomationProvider.dll を繰り返します。C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.

8. をクリックして**新しい参照の追加**、System.dll を選択して、クリックして**OK**します。

9. クリックして**OK**参照の追加の win32clock プロパティ ページを終了します。

 最後に、追加、`STAThreadAttribute`を`_tWinMain`メソッドで使用するため[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

この属性は、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]を初期化した[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]、必要なシングル スレッド アパートメント モデル (STA) を使用する必要があります[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)])。

## <a name="create-a-windows-presentation-framework-page"></a>Windows Presentation Framework ページを作成します。

次に、定義する DLL を作成、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>します。 作成する最も簡単なことがよくあります、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>としてスタンドアロン アプリケーション、および書き込みとデバッグ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]部分のことです。 クリックすると、プロジェクトを右クリックし、DLL にそのプロジェクトを変換できますが終わったら、**プロパティ**しようとして、アプリケーションや Windows クラス ライブラリに出力の種類を変更します。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dll プロジェクトを結合できます、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 、ソリューションを右クリックしてプロジェクト (1 つのソリューションを 2 つのプロジェクトを含む) – **Add\Existing プロジェクト**します。

それを使用する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]から dll、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プロジェクトの参照を追加する必要があります。

1. Win32clock プロジェクトを右クリックして**参照.**.

2. クリックして**新しい参照の追加**します。

3. **[プロジェクト]** タブをクリックします。WPFClock を選択して、[ok] をクリックします。

4. クリックして**OK**参照の追加の win32clock プロパティ ページを終了します。

## <a name="hwndsource"></a>HwndSource

次に、<xref:System.Windows.Interop.HwndSource>させる、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> HWND のようになります。 C++ ファイルには、このコード ブロックを追加します。

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

 これは、長いが、いくつか説明を使用できるコードです。 最初の部分では、すべての呼び出しを完全に修飾する必要はありませんように各種の句は。

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 作成する関数を定義し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ、put、<xref:System.Windows.Interop.HwndSource>および HWND を返します。

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

最初に作成、<xref:System.Windows.Interop.HwndSource>パラメーターを持つ、CreateWindow に似ています。

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

作成し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ クラスのコンス トラクターを呼び出して。

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

ページに接続して、 <xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 最後の行での HWND を返すと、 <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Hwnd を配置

含む HWND をしたら、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時計の内部には、その HWND を配置する必要があります、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ダイアログ。 そのサイズと場所を渡す場合だけ、HWND を配置する場所がわかっている場合、`GetHwnd`前に定義する関数。 Hwnd のいずれかが配置されていることはよくわかっていません、ダイアログ ボックスを定義するリソース ファイルを使用します。 使用することができます、[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]にダイアログ エディター、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]スタティック コントロール、クロックを移動する (「Insert 制ここで」)、配置する際に使用、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クロック。

WM_INITDIALOG を処理する場所を使用する`GetDlgItem`静的なプレース ホルダーの HWND を取得します。

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

計算する静的なプレース ホルダーの位置とサイズ配置できるように、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]その場所にクロックします。

RECT 四角形。

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

静的なプレース ホルダーが非表示します。

```cpp
ShowWindow(placeholder, SW_HIDE);
```

作成し、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND をその場所でのクロックします。

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

チュートリアルの興味深いにして、実数を生成するために[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クロックを作成する必要が、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールをこの時点でクロックします。 分離コードで、いくつかのイベント ハンドラーを持つため、マークアップで行うことができます。 以降、このチュートリアルは、相互運用の概要と、コントロールのデザインはありませんが、完了のコード、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クロックが提供されるここでは不連続の手順ビルドまたは各部分が何を意味せず、コードのブロックとして。 自由に外観やコントロールの機能を変更するには、このコードを実験できます。

マークアップを次に示します。

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

付随する分離コードを次に示します。

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

最終的な結果は、ようになります。

![最終的な結果の日付と時刻のプロパティ ダイアログ ボックス](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

このスクリーン ショットを生成するコードに、最終結果を比較するを参照してください。 [Win32 クロックの相互運用性サンプル](https://go.microsoft.com/fwlink/?LinkID=160051)します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.HwndSource>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [Win32 相互運用のクロックのサンプル](https://go.microsoft.com/fwlink/?LinkID=160051)
