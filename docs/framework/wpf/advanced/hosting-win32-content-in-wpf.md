---
title: WPF での Win32 コンテンツのホスト
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: 8773cac1e421ecdca036e88d79797dae16f72b17
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055080"
---
# <a name="hosting-win32-content-in-wpf"></a>WPF での Win32 コンテンツのホスト

## <a name="prerequisites"></a>必須コンポーネント

参照してください[WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)します。

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Windows Presentation Framework (HwndHost) 内で Win32 のチュートリアル

再利用する[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]内のコンテンツ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションに、 <xref:System.Windows.Interop.HwndHost>、Hwnd のようになりますが、コントロールは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。 ような<xref:System.Windows.Interop.HwndSource>、<xref:System.Windows.Interop.HwndHost>が簡単に使用する: から派生<xref:System.Windows.Interop.HwndHost>実装と`BuildWindowCore`と`DestroyWindowCore`メソッドのインスタンスを作成し、<xref:System.Windows.Interop.HwndHost>クラスを派生し、その内部に配置、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。

場合、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ロジックがすでにをコントロールとしてパッケージ化された、`BuildWindowCore`実装はへの呼び出しよりも少し`CreateWindow`します。 たとえば、作成するため、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]の LISTBOX コントロール[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:

```cpp
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
    HWND handle = CreateWindowEx(0, L"LISTBOX",
    L"this is a Win32 listbox",
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY
    | WS_VSCROLL | WS_BORDER,
    0, 0, // x, y
    30, 70, // height, width
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd
    0, // hmenu
    0, // hinstance
    0); // lparam

    return HandleRef(this, IntPtr(handle));
}

virtual void DestroyWindowCore(HandleRef hwnd) override {
    // HwndHost will dispose the hwnd for us
}
```

しかし、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]コードでは自己完結型ではそれほど大きくありませんか? そのため、作成できる場合、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  ダイアログ ボックスしより大きなにそのコンテンツを埋め込む[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。 これでサンプルを示します[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]と[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]が、これは別の言語でまたはコマンドラインで実行することも、します。

単純なダイアログ ボックスがコンパイルを開始、 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]プロジェクト。

次に、大きい方に、ダイアログの導入[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。

- コンパイル、[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]管理対象として (`/clr`)

- コントロールに、ダイアログ ボックスを有効にします。

- 派生クラスを定義<xref:System.Windows.Interop.HwndHost>で`BuildWindowCore`と`DestroyWindowCore`メソッド

- オーバーライド`TranslateAccelerator`ダイアログ キーを処理するメソッド

- オーバーライド`TabInto`をタブ移動をサポートします。

- オーバーライド`OnMnemonic`ニーモニックをサポートするためにメソッド

- インスタンスを作成、<xref:System.Windows.Interop.HwndHost>サブクラス化し、右下に置いてから[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素

### <a name="turn-the-dialog-into-a-control"></a>コントロールに、ダイアログ ボックスを有効にします。

WS_CHILD と DS_CONTROL スタイルを使用して HWND を子にダイアログ ボックスを有効にすることができます。 ダイアログ ボックスが定義されているリソース ファイル (.rc) に移動し、ダイアログ ボックスの定義の先頭を見つけます。

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

2 行目を変更します。

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

このアクションはいない完全にパッケージ化する自己完結型のコントロールです。呼び出す必要がある`IsDialogMessage()`ように[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]、特定のメッセージを処理することができますが、コントロールの変更はもう 1 つの HWND 内のそれらのコントロールを配置することの簡単な方法を提供します。

## <a name="subclass-hwndhost"></a>サブクラス HwndHost

次の名前空間をインポートします。

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

派生クラスを作成し、<xref:System.Windows.Interop.HwndHost>をオーバーライドし、`BuildWindowCore`と`DestroyWindowCore`メソッド。

```cpp
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {
    private:
        HWND dialog;

    protected:
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
            InitializeGlobals();
            dialog = CreateDialog(hInstance,
                MAKEINTRESOURCE(IDD_DIALOG1),
                (HWND) hwndParent.Handle.ToPointer(),
                (DLGPROC) About);
            return HandleRef(this, IntPtr(dialog));
        }

        virtual void DestroyWindowCore(HandleRef hwnd) override {
            // hwnd will be disposed for us
        }
```

ここで使用して、`CreateDialog`コントロールは、実際にダイアログ ボックスを作成します。 これは内部で呼び出される最初のメソッドのいずれかであるため、 [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]、いくつかの標準を実行することも必要があります[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]後で、定義する関数を呼び出すことによって初期化と呼ばれる`InitializeGlobals()`:。

```cpp
bool initialized = false;
    void InitializeGlobals() {
        if (initialized) return;
        initialized = true;

        // TODO: Place code here.
        MSG msg;
        HACCEL hAccelTable;

        // Initialize global strings
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);
        MyRegisterClass(hInstance);
```

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>ダイアログ キーを処理するために TranslateAccelerator メソッドをオーバーライドします。

このサンプルを実行した場合が表示されたら、ダイアログ コントロールがすべて無視処理は、キーボードの機能 ダイアログ ボックスのダイアログ。 今すぐをオーバーライドする必要があります、`TranslateAccelerator`実装 (に由来する`IKeyboardInputSink`、インターフェイスを<xref:System.Windows.Interop.HwndHost>実装)。 アプリケーションは、WM_KEYDOWN および WM_SYSKEYDOWN が受信すると、このメソッドが呼び出されます。

```cpp
#undef TranslateAccelerator
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
            ModifierKeys modifiers) override
        {
            ::MSG m = ConvertMessage(msg);

            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know
            // what to do when it reaches the last tab stop
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
                TraversalRequest^ request = nullptr;

                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
                    // this code should work, but there’s a bug with interop shift-tab in current builds
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);
                }
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);
                }

                if (request != nullptr)
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);

            }

            // Only call IsDialogMessage for keys it will do something with.
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
                switch (m.wParam) {
                    case VK_TAB:
                    case VK_LEFT:
                    case VK_UP:
                    case VK_RIGHT:
                    case VK_DOWN:
                    case VK_EXECUTE:
                    case VK_RETURN:
                    case VK_ESCAPE:
                    case VK_CANCEL:
                        IsDialogMessage(dialog, &m);
                        // IsDialogMessage should be called ProcessDialogMessage --
                        // it processes messages without ever really telling you
                        // if it handled a specific message or not
                        return true;
                }
            }

            return false; // not a key we handled
        }
```

これは、いくつかのより詳細な説明を使用できるようにするために、多くのコードを 1 つのピースです。 最初に、コードを使用して、[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]と[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]マクロ; という名前のマクロが既に存在するかどうかを注意する必要がある`TranslateAccelerator`winuser.h で定義されています。

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

定義するように、`TranslateAccelerator`メソッドおよび not を`TranslateAcceleratorW`メソッド。

同様に、アンマネージ winuser.h MSG とマネージの両方がありますは`Microsoft::Win32::MSG`構造体。 使用して、2 つを区別することができます、 [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::`演算子。

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}

Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:

```cpp
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {
    ::MSG m;
    m.hwnd = (HWND) msg.hwnd.ToPointer();
    m.lParam = (LPARAM) msg.lParam.ToPointer();
    m.message = msg.message;
    m.wParam = (WPARAM) msg.wParam.ToPointer();

    m.time = msg.time;

    POINT pt;
    pt.x = msg.pt_x;
    pt.y = msg.pt_y;
    m.pt = pt;

    return m;
}
```

戻る`TranslateAccelerator`します。 基本的な原則は、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数`IsDialogMessage`、できるだけ多くの作業を行うが`IsDialogMessage`以外のダイアログ ボックスへのアクセスはありません。 過去のダイアログの最後のコントロールのタブ移動ときに、ダイアログの周囲のユーザー タブを実行すると、フォーカスを設定する必要があります、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]呼び出して部分`IKeyboardInputSite::OnNoMoreStops`します。

```cpp
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know
// what to do when it reaches the last tab stop
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
    TraversalRequest^ request = nullptr;

    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);
    }
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);
    }

    if (request != nullptr)
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);
}
```

最後に、`IsDialogMessage` を呼び出します。 役割の 1 つが、`TranslateAccelerator`メソッドは、指示[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]かどうかにキーストロークを処理するかどうか。 入力イベントをトンネル処理しなかった場合や、アプリケーションの残りの部分からバブルです。 キーボード メッセージ処理の特性とでは、入力アーキテクチャの性質を公開するここでは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]します。 残念ながら、`IsDialogMessage`返さない何らかの方法で特定のキーストロークを処理するかどうか。 呼び出す、さらに悪いこと`DispatchMessage()`キーストロークを処理しないでください。  リバース エンジニア リングする必要がありますように`IsDialogMessage`、しか知らないキーを処理するために呼び出すとします。

```cpp
// Only call IsDialogMessage for keys it will do something with.
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
    switch (m.wParam) {
        case VK_TAB:
        case VK_LEFT:
        case VK_UP:
        case VK_RIGHT:
        case VK_DOWN:
        case VK_EXECUTE:
        case VK_RETURN:
        case VK_ESCAPE:
        case VK_CANCEL:
            IsDialogMessage(dialog, &m);
            // IsDialogMessage should be called ProcessDialogMessage --
            // it processes messages without ever really telling you
            // if it handled a specific message or not
            return true;
    }
```

### <a name="override-tabinto-method-to-support-tabbing"></a>この問題のメソッドをオーバーライドしてサポートのタブ移動するには

実装している`TranslateAccelerator`、ユーザーは、周囲 タブ ダイアログ ボックス内でボックスと、大きい値にそのタブ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。 ユーザーがダイアログ ボックスにタブことはできません。 オーバーライドしている問題を解決する`TabInto`:

```cpp
public:
    virtual bool TabInto(TraversalRequest^ request) override {
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
            SetFocus(lastTabStop);
        }
        else {
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
            SetFocus(firstTabStop);
        }
        return true;
    }
```

`TraversalRequest`パラメーターは、タブのアクションは、タブまたは shift キーを押し タブかどうかを示します。

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>ニーモニックをサポートするために OnMnemonic メソッドをオーバーライドします。

キーボードの処理はほぼ完了が 1 つであることはありません – ニーモニックは機能しません。 フォーカス doe がジャンプしなく-f alt キーを押すと場合、"名:"ボックスを編集します。 そのため、オーバーライドして、`OnMnemonic`メソッド。

```cpp
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {
    ::MSG m = ConvertMessage(msg);

    // If it's one of our mnemonics, set focus to the appropriate hwnd
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {
        int dialogitem = 9999;
        switch (m.wParam) {
            case 's': dialogitem = IDOK; break;
            case 'c': dialogitem = IDCANCEL; break;
            case 'f': dialogitem = IDC_EDIT1; break;
            case 'l': dialogitem = IDC_EDIT2; break;
            case 'p': dialogitem = IDC_EDIT3; break;
            case 'a': dialogitem = IDC_EDIT4; break;
            case 'i': dialogitem = IDC_EDIT5; break;
            case 't': dialogitem = IDC_EDIT6; break;
            case 'z': dialogitem = IDC_EDIT7; break;
        }
        if (dialogitem != 9999) {
            HWND hwnd = GetDlgItem(dialog, dialogitem);
            SetFocus(hwnd);
            return true;
        }
    }
    return false; // key unhandled
};
```

なぜ`IsDialogMessage`ここか?  これまでに通知できるようにする必要があります。 同じ問題がある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コードか、キーストロークが処理されるかどうかをコードと`IsDialogMessage`を行うことはできません。 2 つ目の問題があります、ため`IsDialogMessage` ダイアログ ボックス内でフォーカスがある HWND がない場合、ニーモニックの処理を拒否します。

### <a name="instantiate-the-hwndhost-derived-class"></a>インスタンスを作成、HwndHost 派生クラス

最後に、これですべてのキーとタブのサポートができたら、配置できること、<xref:System.Windows.Interop.HwndHost>うち、大きい方に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。 メイン アプリケーションが記述されている場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、適切な場所に配置する最も簡単な方法は、空のままにする、<xref:System.Windows.Controls.Border>要素を配置する、<xref:System.Windows.Interop.HwndHost>します。 ここで作成し、<xref:System.Windows.Controls.Border>という`insertHwndHostHere`:

```xaml
<Window x:Class="WPFApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Windows Presentation Framework Application"
    Loaded="Window1_Loaded"
    >
    <StackPanel>
        <Button Content="WPF button"/>
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>
        <Button Content="WPF button"/>
    </StackPanel>
</Window>
```

残っているはインスタンスを作成するコード シーケンスのことをお勧めを検索し、<xref:System.Windows.Interop.HwndHost>に接続し、<xref:System.Windows.Controls.Border>します。 この例では内に配置することのコンス トラクター、<xref:System.Windows.Window>クラスを派生します。

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

提示されます。

![WPF アプリケーションのスクリーン ショット](./media/interoparch09.PNG "InteropArch09")

## <a name="see-also"></a>関連項目

- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
