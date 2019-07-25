---
title: WPF での Win32 コンテンツのホスト
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: ee260d58cdb4dc971fc32ca5c889b459b6a48489
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484735"
---
# <a name="hosting-win32-content-in-wpf"></a>WPF での Win32 コンテンツのホスト

## <a name="prerequisites"></a>必須コンポーネント

「 [WPF と Win32 の相互運用」を](wpf-and-win32-interoperation.md)参照してください。

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Windows Presentation Framework 内部の Win32 のチュートリアル (HwndHost)

アプリケーション内[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを再利用<xref:System.Windows.Interop.HwndHost>するには、を使用します。これ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、hwnd をコンテンツのように表示するコントロールです。 と<xref:System.Windows.Interop.HwndSource>同様<xref:System.Windows.Interop.HwndHost>に、は簡単に使用でき<xref:System.Windows.Interop.HwndHost>ます。 `BuildWindowCore`から`DestroyWindowCore`派生し、メソッドを<xref:System.Windows.Interop.HwndHost>実装してから、派生クラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をインスタンス化し、その中に配置します。適用.

ロジックが既にコントロールとしてパッケージ化され`BuildWindowCore`ている場合、の実装はの`CreateWindow`呼び出しよりもわずかです。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] たとえば、でC++LISTBOX コントロールを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]作成するには、次のようにします。

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

しかし、コード[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]がそれほど自己完結していないとしたら、 その場合は、ダイアログボックスを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]作成し、その内容をより大きな[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションに埋め込むことができます。 このサンプルでは、 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]とC++でこれを示していますが、別の言語またはコマンドラインでこれを行うこともできます。

[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]プロジェクトにC++コンパイルされた単純なダイアログから始めます。

次に、大規模[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]なアプリケーションにダイアログを導入します。

- をマネージ[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] (`/clr`) としてコンパイルします。

- ダイアログをコントロールに変換する

- メソッドとメソッドを使用<xref:System.Windows.Interop.HwndHost> `BuildWindowCore`して`DestroyWindowCore` 、の派生クラスを定義します。

- メソッド`TranslateAccelerator`をオーバーライドしてダイアログキーを処理します

- Tab `TabInto`キーをサポートするためのオーバーライドメソッド

- ニーモニック`OnMnemonic`をサポートするオーバーライドメソッド

- サブクラス<xref:System.Windows.Interop.HwndHost>をインスタンス化し、右側[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の要素の下に配置する

### <a name="turn-the-dialog-into-a-control"></a>ダイアログをコントロールに変換する

WS_CHILD スタイルと DS_CONTROL スタイルを使用して、ダイアログボックスを子 HWND にすることができます。 ダイアログが定義されているリソースファイル (.rc) に移動し、ダイアログの定義の先頭を見つけます。

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

2番目の行を次のように変更します。

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

この操作では、自己完結型のコントロールに完全にパッケージ化されません。では、特定の`IsDialogMessage()`メッセージ[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]を処理できるようにを呼び出す必要がありますが、コントロールを変更すると、そのコントロールを別の HWND 内に簡単に配置できます。

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

次に、の<xref:System.Windows.Interop.HwndHost>派生クラスを作成し、メソッド`BuildWindowCore`と`DestroyWindowCore`メソッドをオーバーライドします。

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

ここでは、 `CreateDialog`を使用して、実際にはコントロールであるダイアログボックスを作成します。 これはの[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]内部で呼び出された最初のメソッドの1つであるため、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]後`InitializeGlobals()`で定義する関数を呼び出すことによって、標準の初期化も実行する必要があります。

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>TranslateAccelerator メソッドをオーバーライドしてダイアログキーを処理します

このサンプルを今実行した場合、ダイアログコントロールが表示されますが、ダイアログボックスを機能させるためのダイアログボックスを表示するすべてのキーボード処理が無視されます。 ここで`TranslateAccelerator` `IKeyboardInputSink`、実装 (を実装する<xref:System.Windows.Interop.HwndHost>インターフェイス) をオーバーライドする必要があります。 このメソッドは、アプリケーションが WM_KEYDOWN と WM_SYSKEYDOWN を受け取ると呼び出されます。

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

これは、1つの部分に多くのコードがあるため、より詳細な説明を使用できます。 まず、マクロとC++ C++マクロを使用するコードです。winuser. h で定義されているという`TranslateAccelerator`名前のマクロが既に存在することに注意する必要があります。

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

したがって、メソッドでは`TranslateAccelerator` `TranslateAcceleratorW`なく、メソッドを定義してください。

同様に、アンマネージ winuser .h メッセージとマネージ`Microsoft::Win32::MSG`構造体の両方があります。 `::`演算子を使用してC++ 、2つを明確に区別できます。

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

に`TranslateAccelerator`戻ります。 基本的な原則は、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数`IsDialogMessage`を呼び出して、可能な限り多くの作業を`IsDialogMessage`行うことですが、ダイアログの外部にアクセスすることはできません。 ダイアログの周囲のユーザータブとして、ダイアログの最後のコントロールの後で tab キーを実行する場合は、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を呼び出し`IKeyboardInputSite::OnNoMoreStops`て、その部分にフォーカスを設定する必要があります。

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

最後に、`IsDialogMessage` を呼び出します。 しかし、 `TranslateAccelerator`メソッドの役割の1つは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]キーストロークを処理したかどうかを通知することです。 処理しなかった場合、入力イベントは、アプリケーションの他の部分をトンネルおよびバブルできます。 ここでは、のキーボード messange 処理の特性と、の入力アーキテクチャ[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]の性質を公開します。 残念ながら`IsDialogMessage` 、は、特定のキー入力を処理するかどうかを何も返しません。 さらに悪いことに、 `DispatchMessage()`キーストロークを処理する必要はありません。  そのため、リバースエンジニアリング`IsDialogMessage`を行う必要があります。これは、処理されることがわかっているキーに対してのみ呼び出す必要があります。

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

### <a name="override-tabinto-method-to-support-tabbing"></a>タブ移動をサポートするために TabInto メソッドをオーバーライドする

実装`TranslateAccelerator`が完了したので、ユーザーはダイアログボックス内を tab キーを使用して、より大きな[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションに tab キーを移動できます。 ただし、ユーザーがダイアログボックスに戻ることはできません。 これを解決するには`TabInto`、次のようにオーバーライドします。

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

パラメーター `TraversalRequest`を指定すると、タブ操作がタブまたは shift タブのどちらであるかがわかります。

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>OnMnemonic メソッドをオーバーライドしてニーモニックをサポートする

キーボードの処理はほぼ完了していますが、不足しているものがあります。ニーモニックが機能しません。 ユーザーが alt キーを押しながら F キーを押すと、"First name:" という編集ボックスにフォーカスが移動します。 そのため、 `OnMnemonic`メソッドをオーバーライドします。

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

ここでは`IsDialogMessage`何を呼ぶのでしょうか。  前と同じ問題が発生しています。コードでキー入力が[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]処理されたかどうか`IsDialogMessage`をコードに通知できる必要があり、そうすることはできません。 また、は、フォーカスされて`IsDialogMessage`いる HWND がダイアログボックス内にない場合にニーモニックの処理が拒否されるため、2つ目の問題もあります。

### <a name="instantiate-the-hwndhost-derived-class"></a>HwndHost 派生クラスをインスタンス化する

最後に、すべてのキーとタブのサポートが整ったので、をより<xref:System.Windows.Interop.HwndHost>大きな[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションに配置できます。 メインアプリケーションがに[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]記述されている場合、適切な場所に配置する最も簡単な方法は、 <xref:System.Windows.Controls.Border> <xref:System.Windows.Interop.HwndHost>を配置する場所に空の要素を残しておくことです。 ここでは、 <xref:System.Windows.Controls.Border>と`insertHwndHostHere`いう名前のを作成します。

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

次に、 <xref:System.Windows.Interop.HwndHost>をインスタンス化してに接続<xref:System.Windows.Controls.Border>するためのコードシーケンス内の適切な場所を見つけます。 この例では、 <xref:System.Windows.Window>派生クラスのコンストラクター内に配置します。

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

次のようになります。

![実行中の WPF アプリのスクリーンショット。](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a>関連項目

- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
