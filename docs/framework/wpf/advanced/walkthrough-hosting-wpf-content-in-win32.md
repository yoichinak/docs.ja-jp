---
title: Win32 で WPF コンテンツをホストする
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 8a5d556abf49c9c1f49e7853e752ebc5248d1101
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186067"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>チュートリアル: Win32 での WPF コンテンツのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただし、Win32 コードに多大な投資を行う場合は、元のコード[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を書き換えるよりも、アプリケーションに機能を追加した方が効果的な場合があります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、Win32[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウでコンテンツをホストするための簡単なメカニズムを提供します。  
  
 このチュートリアルでは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][、Win32 ウィンドウでコンテンツをホストするサンプル アプリケーション、Win32 ウィンドウサンプルでの WPF コンテンツのホスティング](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage)を記述する方法について説明します。 このサンプルを拡張して、任意の Win32 ウィンドウをホストできます。 マネージ コードとアンマネージ コードの混在が含まれるため、アプリケーションは C++/CLI で記述されます。  

<a name="requirements"></a>
## <a name="requirements"></a>必要条件  
 このチュートリアルでは、Win32 プログラミング[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と Win32 プログラミングの両方に関する基本的な知識があることを前提としています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プログラミングの基本的な概要については、「[はじめに](../getting-started/index.md)」を参照してください。 Win32 プログラミングの概要については、この問題に関する多数の書籍、特にチャールズ ペトゾルドの*プログラミング Windows を*参照する必要があります。  
  
 このチュートリアルに付属するサンプルは C++/CLI で実装されているため、このチュートリアルでは、C++ を使用した Windows API のプログラミングとマネージ コード プログラミングの理解に精通していることを前提としています。 C++/CLI に精通することは役に立ちますが、必須ではありません。  
  
> [!NOTE]
> このチュートリアルには、関連するサンプルからのコード例が多数含まれています。 しかし、読みやすくするため、完全なサンプル コードは含まれていません。 完全なサンプル コードについては、「 [Win32 ウィンドウのサンプルでの WPF コンテンツのホスト](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage)」を参照してください。  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>基本手順  
 このセクションでは、Win32 ウィンドウでコンテンツ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をホストするための基本的な手順について説明します。 残りのセクションでは、各手順の詳細について説明します。  
  
 Win32[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウでコンテンツをホストするキーは、<xref:System.Windows.Interop.HwndSource>クラスです。 このクラスは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、Win32 ウィンドウにコンテンツをラップし、子ウィンドウとしてユーザー[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]に組み込むことができます。 次の方法では、Win32 と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]単一のアプリケーションを組み合わせています。  
  
1. コンテンツを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マネージ クラスとして実装します。  
  
2. C++/CLI を使用して Windows アプリケーションを実装します。 既存のアプリケーションとアンマネージ C++ コードから開始する場合は、通常、プロジェクト設定を変更してコンパイラ フラグを含めることで、`/clr`マネージ コードを呼び出すことができます。  
  
3. スレッド処理モデルをシングル スレッド アパートメント (STA: Single Threaded Apartment) に設定します。  
  
4. ウィンドウ プロシージャで[WM_CREATE](/windows/desktop/winmsg/wm-create)通知を処理し、次の操作を行います。  
  
    1. 新しい <xref:System.Windows.Interop.HwndSource> オブジェクトを、親ウィンドウがその `parent` パラメーターとなるように指定して作成します。  
  
    2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ クラスのインスタンスを作成します。  
  
    3. コンテンツ オブジェクトへの参照[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を<xref:System.Windows.Interop.HwndSource.RootVisual%2A><xref:System.Windows.Interop.HwndSource>のプロパティに割り当てます。  
  
    4. コンテンツの HWND を取得します。 <xref:System.Windows.Interop.HwndSource.Handle%2A> オブジェクトの <xref:System.Windows.Interop.HwndSource> プロパティにウィンドウ ハンドル (HWND) が格納されます。 アプリケーションのアンマネージ部分で使用できる HWND を取得するには、`Handle.ToPointer()` を HWND にキャストします。  
  
5. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照を保持する静的フィールドを含むマネージド クラスを実装します。 このクラスを使用すると、Win32[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コードからコンテンツへの参照を取得できます。  
  
6. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを静的フィールドに割り当てます。  
  
7. 1 つ以上[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のイベントにハンドラーをアタッチして、コンテンツから通知を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]受信します。  
  
8. 静的フィールドに格納した参照を使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツと通信し、プロパティの設定などを行います。  
  
> [!NOTE]
> コンテンツの実装にも[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]使用できます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 ただし、ダイナミック リンク ライブラリ (DLL) として個別にコンパイルし、Win32 アプリケーションからその DLL を参照する必要があります。 手順の残りの部分は、前述の手順と同様です。

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装
 このセクションでは、基本的な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Win32 アプリケーションでコンテンツをホストする方法について説明します。 コンテンツ自体は、C++/CLI でマネージ クラスとして実装されます。 ほとんどの部分が、簡単な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプログラミングです。 コンテンツ実装の主要な側面については、「 WPF[コンテンツの実装](#implementing_the_wpf_page)」を参照してください。

- [基本的なアプリケーション](#the_basic_application)

- [WPF コンテンツのホスティング](#hosting_the_wpf_page)

- [WPF コンテンツへの参照の保持](#holding_a_reference)

- [WPF コンテンツとの通信](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>基本的なアプリケーション
 ホスト アプリケーションの開始点は、Visual Studio 2005 テンプレートを作成することです。

1. Visual Studio 2005 を開き、[**ファイル]** メニューの **[新しいプロジェクト**] を選択します。

2. Visual C++ プロジェクトの種類の一覧から **[Win32]** を選択します。 既定の言語が C++ でない場合は、これらのプロジェクトの種類が **[その他の言語**] の下にあります。

3. **Win32 プロジェクト**テンプレートを選択し、プロジェクトに名前を割り当て **、[OK]** をクリックして**Win32 アプリケーション ウィザード**を起動します。

4. ウィザードの既定の設定をそのまま使用し、[完了]**を**クリックしてプロジェクトを開始します。

 テンプレートは、次の基本的な Win32 アプリケーションを作成します。

- アプリケーションのエントリ ポイント。

- 関連するウィンドウ プロシージャ (WndProc) を含むウィンドウ。

- **ファイル**と**ヘルプ**の見出しを含むメニュー。 **[ファイル]** メニューには、アプリケーションを閉じる**終了**項目があります。 **[ヘルプ**] メニューには、簡単なダイアログ ボックスを起動する **[About]** 項目があります。

 コンテンツをホストするコードの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]作成を開始する前に、基本テンプレートに 2 つの変更を加える必要があります。

 1 つ目は、プロジェクトをマネージド コードとしてコンパイルすることです。 既定では、プロジェクトはアンマネージ コードとしてコンパイルされます。 ただし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] はマネージド コードで実装されているため、プロジェクトは状況に応じてコンパイルする必要があります。

1. **ソリューション エクスプローラー**でプロジェクト名を右クリックし、コンテキスト メニューから **[プロパティ**] を選択して[**プロパティ ページ**] ダイアログ ボックスを開きます。

2. 左側のペインのツリービューから[**構成プロパティ]** を選択します。

3. 右側のウィンドウの [**プロジェクトの既定値]** ボックスの一覧から [**共通言語ランタイム**のサポート] を選択します。

4. ドロップダウン リスト ボックスから **[共通言語ランタイム サポート (/clr)] を**選択します。

> [!NOTE]
> このコンパイラ フラグを使用すると、アプリケーションでマネージド コードを使用できますが、アンマネージド コードは以前と同様にコンパイルされます。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、シングル スレッド アパートメント (STA) スレッド処理モデルを使用します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ コードを適切に処理するには、エントリ ポイントに属性を適用して、アプリケーションのスレッド モデルを STA に設定する必要があります。

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>WPF コンテンツのホスティング
 内容[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、単純なアドレス入力アプリケーションです。 それは、ユーザー名やアドレスなどを取得する複数の <xref:System.Windows.Controls.TextBox> コントロールで構成されています。 **[OK]** <xref:System.Windows.Controls.Button>と [**キャンセル]** の 2 つのコントロールもあります。 ユーザーが **[OK]** をクリックすると、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>ボタンのイベント ハンドラはコントロールから<xref:System.Windows.Controls.TextBox>データを収集し、対応するプロパティに割り当て、カスタム`OnButtonClicked`イベントを発生させます。 ユーザーが [**キャンセル**] をクリックすると`OnButtonClicked`、 ハンドラは 単に を発生させます。 `OnButtonClicked` のイベント引数オブジェクトには、どのボタンをクリックしたかを示すブール型フィールドが含まれています。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツをホストするコードは、ホスト ウィンドウの[WM_CREATE](/windows/desktop/winmsg/wm-create)通知のハンドラーに実装されます。

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 この`GetHwnd`メソッドは、サイズと位置情報に加えて、親ウィンドウ ハンドルを受け取り、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストされたコンテンツのウィンドウ ハンドルを返します。

> [!NOTE]
> `#using` 名前空間に `System::Windows::Interop` ディレクティブを使用することはできません。 使用すると、その名前空間の <xref:System.Windows.Interop.MSG> 構造体と winuser.h で宣言した MSG 構造体の間で名前の競合が発生します。 代わりに、その名前空間のコンテンツにアクセスするための完全修飾名を使用する必要があります。

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 アプリケーション ウィンドウで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツを直接ホストすることはできません。 代わりに、まず <xref:System.Windows.Interop.HwndSource> コンテンツをラップするための [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトを作成します。 このオブジェクトは、基本的にはコンテンツをホストするように設計された[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウです。 親ウィンドウで<xref:System.Windows.Interop.HwndSource>オブジェクトをホストするには、アプリケーションの一部である Win32 ウィンドウの子として作成します。 コンストラクター<xref:System.Windows.Interop.HwndSource>のパラメーターには、Win32 子ウィンドウを作成するときに CreateWindow に渡す情報とほぼ同じ情報が含まれています。

 次に、コンテンツ オブジェクトの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インスタンスを作成します。 この場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツは C++/CLI を使用して`WPFPage`個別のクラスとして実装されます。 さらに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で実装することもできます。 ただし、そのためには、別のプロジェクトを設定し、コンテンツを DLL[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]としてビルドする必要があります。 その DLL への参照をプロジェクトに追加し、その参照を使用してコンテンツのインスタンスを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]作成できます。

 子ウィンドウに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツを表示するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Interop.HwndSource.RootVisual%2A><xref:System.Windows.Interop.HwndSource>のプロパティにコンテンツへの参照を割り当てます。

 次のコード行は、イベント ハンドラー `WPFButtonClicked` を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの `OnButtonClicked` イベントにアタッチしています。 このハンドラーは、ユーザーが **[OK] または**[**キャンセル**] ボタンをクリックしたときに呼び出されます。 このイベント ハンドラーcommunicating_with_the_WPF詳細については、[コンテンツ](#communicating_with_the_page)を参照してください。

 示されているコードの最後の行は、<xref:System.Windows.Interop.HwndSource> オブジェクトに関連付けられているウィンドウ ハンドル (HWND) を返します。 このハンドルは Win32 コードから使用してホストされたウィンドウにメッセージを送信できますが、このハンドルはホストされたウィンドウに送信されません。 <xref:System.Windows.Interop.HwndSource> オブジェクトは、メッセージを受信するたびにイベントを発生させます。 メッセージを処理するには、<xref:System.Windows.Interop.HwndSource.AddHook%2A> メソッドを呼び出してメッセージ ハンドラーをアタッチしてから、そのハンドラーでメッセージを処理します。

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>WPF コンテンツへの参照の保持
 多くのアプリケーションでは、後で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツと通信することができます。 たとえば、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのプロパティを変更したり、場合によっては <xref:System.Windows.Interop.HwndSource> オブジェクトが異なる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストするようにしたりできます。 そのためには、<xref:System.Windows.Interop.HwndSource> オブジェクトまたは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照が必要です。 <xref:System.Windows.Interop.HwndSource> オブジェクトと関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、ウィンドウ ハンドルを破棄するまでメモリに残ります。 ただし、<xref:System.Windows.Interop.HwndSource> オブジェクトに割り当てる変数は、ウィンドウ プロシージャから戻ると同時にスコープの外に出ます。 Win32 アプリケーションでこの問題を処理する一例として、静的変数またはグローバル変数を使用します。 残念ながら、このような変数の種類に対してマネージド オブジェクトを割り当てることはできません。 <xref:System.Windows.Interop.HwndSource> オブジェクトに関連付けられているウィンドウ ハンドルを、グローバル変数または静的変数に割り当てることができますが、オブジェクト自体にアクセスすることはできません。

 この問題の最も簡単な解決法は、静的フィールドのセットを含むマネージド クラスを実装して、アクセスが必要なすべてのマネージド オブジェクトへの参照を保持することです。 サンプルでは、`WPFPageHost` クラスを使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照、および後でユーザーが変更する可能性があるプロパティの数の初期値を保持します。 これは、ヘッダーで定義します。

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 `GetHwnd` 関数の後半部分では、後に、`myPage` がスコープ内にある間に使用するため、対象のフィールドに値を割り当てます。

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>WPF コンテンツとの通信
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツとの通信には次の 2 種類があります。 ユーザーが **[OK]** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]または [**キャンセル]** ボタンをクリックすると、アプリケーションはコンテンツから情報を受け取ります。 アプリケーションには、背景色や既定のフォント サイズなどのさまざまな [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] コンテンツのプロパティをユーザーが変更できるようにする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] があります。

 前述のように、ユーザーがいずれかのボタンをクリックすると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは `OnButtonClicked` イベントを発生させます。 アプリケーションは、これらの通知を受信するため、このイベントにハンドラーをアタッチします。 **[OK]** ボタンがクリックされた場合、ハンドラーはコンテンツからユーザー情報[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を取得し、静的コントロールのセットに表示します。

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 ハンドラーは、カスタム イベント引数オブジェクトを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコンテンツ、`MyPageEventArgs` から受信します。 [OK]`IsOK`ボタンがクリックされた`true`場合、**OK**および`false`[**キャンセル**] ボタンがクリックされた場合、オブジェクトのプロパティは次の値に設定されます。

 **[OK]** ボタンがクリックされた場合、ハンドラーはコンテナー クラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]からコンテンツへの参照を取得します。 その後、関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ プロパティが保持するユーザー情報を収集し、静的コントロールを使用して親ウィンドウに情報を表示します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ データはマネージ文字列の形式であるため、Win32 コントロールで使用するためにマーシャリングする必要があります。 **[キャンセル]** ボタンがクリックされた場合、ハンドラーは静的コントロールからデータを消去します。

 アプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] には、ユーザーが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの背景色を変更できるようにするラジオ ボタンのセット、および複数のフォント関連のプロパティが用意されています。 次の例は、アプリケーションのウィンドウ プロシージャ (WndProc)、および背景色など、各種のメッセージに対してさまざまなプロパティを設定するそのプロシージャのメッセージ処理からの抜粋です。 その他は類似しているため、示していません。 詳細とコンテキストについては、完全なサンプルを参照してください。

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 背景色を設定するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] から `hostedPage` コンテンツ (`WPFPageHost`) への参照を取得して、背景色のプロパティを適切な色に設定します。 サンプルでは、元の色、明るい緑、または明るいサーモン色の 3 つの色のオプションを使用します。 元の背景色は静的フィールドとして `WPFPageHost` クラスに格納されます。 他の 2 つの色を設定するには、新しい <xref:System.Windows.Media.SolidColorBrush> オブジェクトを作成して、<xref:System.Windows.Media.Colors> オブジェクトからコンストラクターに静的な色の値を渡します。

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>WPF ページの実装
 実際の実装を知ら[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]なくても、コンテンツをホストして使用できます。 コンテンツが[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]別の DLL にパッケージ化されている場合は、共通言語ランタイム (CLR) 言語でビルドされている可能性があります。 次に、サンプルで使用される C++/CLI 実装の簡単なチュートリアルを示します。 このセクションには、次のサブセクションが含まれています。

- [レイアウト](#page_layout)

- [データをホスト ウィンドウに返す](#returning_data_to_window)

- [WPF のプロパティを設定する](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>[レイアウト]
 コンテンツ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]内の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素は、5<xref:System.Windows.Controls.TextBox>つのコントロールで構成<xref:System.Windows.Controls.Label>され、関連付けられたコントロール (名前、住所、市区町村、都道府県、および Zip) が関連付けられます。 **[OK]** <xref:System.Windows.Controls.Button>と [**キャンセル]** の 2 つのコントロールもあります。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは `WPFPage` クラスに実装されています。 レイアウトは、<xref:System.Windows.Controls.Grid> レイアウト要素で処理されます。 クラスは <xref:System.Windows.Controls.Grid> から継承されます。これにより、クラスは効果的に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのルート要素になります。

 コンテンツ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンストラクターは、必要な幅と高さを受け取<xref:System.Windows.Controls.Grid>り、それに応じてサイズを変更します。 次<xref:System.Windows.Controls.ColumnDefinition>に、オブジェクトの<xref:System.Windows.Controls.RowDefinition>セットを作成し、オブジェクトベース<xref:System.Windows.Controls.Grid><xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>と<xref:System.Windows.Controls.Grid.RowDefinitions%2A>コレクションにそれぞれ追加することで、基本的なレイアウトを定義します。 これにより、5 つの行と、7 つの列のグリッドが定義され、セルの内容によって大きさが決定します。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 次に、コンストラクターは [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を <xref:System.Windows.Controls.Grid> に追加します。 最初の要素はタイトルのテキストです。これは、グリッドの 1 行目の中央に表示される <xref:System.Windows.Controls.Label> コントロールです。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 次の行には、名前の <xref:System.Windows.Controls.Label> コントロールと関連する <xref:System.Windows.Controls.TextBox> コントロールが格納されます。 ラベルとテキスト ボックスの各ペアに同じコードが使用されるため、コードはプライベート メソッドのペアに配置され、5 つのラベルとテキスト ボックスのペアすべてに使用されます。 メソッドは適切な制御を作成し、<xref:System.Windows.Controls.Grid> クラスの静的な <xref:System.Windows.Controls.Grid.SetColumn%2A> および <xref:System.Windows.Controls.Grid.SetRow%2A> メソッドを呼び出して、適切なセルにコントロールを配置します。 コントロールが作成されると、サンプルは <xref:System.Windows.Controls.UIElementCollection.Add%2A> の <xref:System.Windows.Controls.Panel.Children%2A> プロパティの <xref:System.Windows.Controls.Grid> メソッドを呼び出して、グリッドにコントロールを追加します。 残りのラベルとテキスト ボックスのペアを追加するコードは似ています。 詳細については、サンプル コードを参照してください。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 2 つのメソッドの実装は、次のとおりです。

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 最後に、このサンプルでは **[OK]** ボタンと **[キャンセル]** ボタンを追加し<xref:System.Windows.Controls.Primitives.ButtonBase.Click>、イベント ハンドラをイベントにアタッチします。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>データをホスト ウィンドウに返す
 いずれかのボタンをクリックすると、その <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントが発生します。 ホスト ウィンドウはこれらのイベントにハンドラーをアタッチして、<xref:System.Windows.Controls.TextBox> コントロールから直接データを取得します。 サンプルは、いくぶん直接的ではない方法を使用します。 コンテンツ内の<xref:System.Windows.Controls.Primitives.ButtonBase.Click>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を処理し、カスタム イベント`OnButtonClicked`を発生させ、コンテンツに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]通知します。 これにより、ホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に通知する前に、コンテンツがパラメータ検証を行うことができます。 ハンドラーは、<xref:System.Windows.Controls.TextBox> コントロールからテキストを取得し、パブリック プロパティに割り当てます。ここからホストは情報を取得します。

 WPFPage.h でのイベント宣言:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 WPFPage.cpp での <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラー:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>WPF のプロパティを設定する
 Win32 ホストを使用すると、ユーザーは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複数のコンテンツ プロパティを変更できます。 Win32 側から見ると、プロパティを変更するだけです。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコンテンツ クラスの実装はいくらか複雑になります。これは、全コントロールのフォントを制御する 1 つのグローバル プロパティがないためです。 代わりに、各コントロールの適切なプロパティは、プロパティの set アクセサーで変更されます。 プロパティのコードの例を次に`DefaultFontFamily`示します。 プロパティを設定すると、プライベート メソッドが呼び出され、さまざまなコントロールに <xref:System.Windows.Controls.Control.FontFamily%2A> プロパティが設定されます。

 WPFPage.h から:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 WPFPage.cpp から:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.HwndSource>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
