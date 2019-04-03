---
title: 'チュートリアル: Win32 での WPF コンテンツのホスト'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 1f1ac68e49b5f84a41e3091b1a81010e7aa7cc0b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363164"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>チュートリアル: Win32 での WPF コンテンツのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただし、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] コードにかなりの投資がある場合は、元のコードを書き換えるより、アプリケーションに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の機能を追加するほうがより効果的であることがあります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ホストするための簡単なメカニズムを提供します。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ。  
  
 このチュートリアルは、サンプル アプリケーションを記述する方法を説明します[Win32 ウィンドウのサンプルで WPF コンテンツをホストしている](https://go.microsoft.com/fwlink/?LinkID=160004)、そのホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ。 このサンプルを拡張すると、いずれの [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウでもホストできます。 マネージド コードとアンマネージド コードの混在が関係しているため、このアプリケーションは [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] で記述されます。  
  
 
  
<a name="requirements"></a>   
## <a name="requirements"></a>必要条件  
 このチュートリアルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プログラミングの基礎知識があることを前提としています。 基本的な事柄[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プログラミングを参照してください[Getting Started](../getting-started/index.md)します。 概要については[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プログラミングでは、参照すること、この主題に関する数多くの書籍の特に*プログラミング Windows* Charles Petzold 著。  
  
 このチュートリアルに付属するサンプルがで実装されているため[!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]、このチュートリアルの使用に関する知識を前提としています[!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]プログラムに、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]マネージ コード プログラミングの理解。 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] の知識があることは、役立ちますが、必須ではありません。  
  
> [!NOTE]
>  このチュートリアルには、関連するサンプルからのコード例が多数含まれています。 しかし、読みやすくするため、完全なサンプル コードは含まれていません。 完全なサンプル コードで、次を参照してください。 [Win32 ウィンドウのサンプルで WPF のコンテンツをホストしている](https://go.microsoft.com/fwlink/?LinkID=160004)します。  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>基本手順  
 このセクションで説明を使用する基本手順ホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ。 残りのセクションでは、各手順の詳細について説明します。  
  
 ホストする鍵[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウは、<xref:System.Windows.Interop.HwndSource>クラス。 このクラスは、ラップ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でコンテンツを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]に組み込むことができるように、ウィンドウ、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]子ウィンドウとして。 次の方法では、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を単一のアプリケーションに統合します。  
  
1.  実装、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マネージ クラスとしてコンテンツ。  
  
2.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションを [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] で実装します。 既存のアプリケーションとアンマネージドの [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] コードで使用を開始する場合、通常は、プロジェクトの設定を `/clr` コンパイラ フラグを含めるように変更して、マネージド コードを呼び出せるようにします。  
  
3.  スレッド処理モデルをシングル スレッド アパートメント (STA: Single Threaded Apartment) に設定します。  
  
4.  処理、 [WM_CREATE](/windows/desktop/winmsg/wm-create)ウィンドウ プロシージャと次の操作で通知します。  
  
    1.  新しい <xref:System.Windows.Interop.HwndSource> オブジェクトを、親ウィンドウがその `parent` パラメーターとなるように指定して作成します。  
  
    2.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ クラスのインスタンスを作成します。  
  
    3.  参照を割り当てる、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ オブジェクト、<xref:System.Windows.Interop.HwndSource.RootVisual%2A>のプロパティ、<xref:System.Windows.Interop.HwndSource>します。  
  
    4.  コンテンツの HWND を取得します。 <xref:System.Windows.Interop.HwndSource.Handle%2A> オブジェクトの <xref:System.Windows.Interop.HwndSource> プロパティにウィンドウ ハンドル (HWND) が格納されます。 アプリケーションのアンマネージ部分で使用できる HWND を取得するには、`Handle.ToPointer()` を HWND にキャストします。  
  
5.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照を保持する静的フィールドを含むマネージド クラスを実装します。 このクラスを使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コードから [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コンテンツへの参照を取得できるようになります。  
  
6.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを静的フィールドに割り当てます。  
  
7.  通知を受信、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツを 1 つまたは複数のハンドラーをアタッチすることにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント。  
  
8.  静的フィールドに格納した参照を使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツと通信し、プロパティの設定などを行います。  
  
> [!NOTE]
>  使用することも[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]実装するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。 ただし、このコンテンツは [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] として別にコンパイルしてから、その [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] に [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションから参照する必要があります。 手順の残りの部分は、前述の手順と同様です。

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装
 このセクションの説明をホストする方法[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で基本的なコンテンツ[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーション。 コンテンツ自体は、マネージド クラスとして [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] に実装されます。 ほとんどの部分が、簡単な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプログラミングです。 コンテンツの実装の重要な側面は、後ほど[WPF コンテンツを実装する](#implementing_the_wpf_page)します。

<a name="autoNestedSectionsOUTLINE1"></a>
-   [基本的なアプリケーション](#the_basic_application)

-   [WPF コンテンツのホスティング](#hosting_the_wpf_page)

-   [WPF コンテンツへの参照の保持](#holding_a_reference)

-   [WPF コンテンツとの通信](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>基本的なアプリケーション
 ホスト アプリケーションの開始点は、Visual Studio 2005 テンプレートを作成しました。

1.  Visual Studio 2005 を開き、選択**新しいプロジェクト**から、**ファイル**メニュー。

2.  選択**Win32**の一覧から[!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)]プロジェクトの種類。 既定の言語がない場合[!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)]、これらのプロジェクト タイプの下に表示されます**他の言語**します。

3.  選択、 **Win32 プロジェクト**テンプレート、プロジェクトに名前を割り当てるし、をクリックして**OK**を起動する、 **Win32 アプリケーション ウィザード**。

4.  ウィザードの既定の設定をそのまま使用し、をクリックして**完了**プロジェクトを開始します。

 このテンプレートは、次のような基本的な [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションを作成します。

-   アプリケーションのエントリ ポイント。

-   関連するウィンドウ プロシージャ (WndProc) を含むウィンドウ。

-   持つメニュー**ファイル**と**ヘルプ**見出し。 **ファイル**メニューがあります、**終了**項目をアプリケーションを閉じます。 **ヘルプ**メニューがあります、**について**簡単なダイアログ ボックスを起動する項目。

 ホストにコードを記述する前に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ、する必要がある 2 つの基本的なテンプレートを変更します。

 1 つ目は、プロジェクトをマネージド コードとしてコンパイルすることです。 既定では、プロジェクトはアンマネージ コードとしてコンパイルされます。 ただし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] はマネージド コードで実装されているため、プロジェクトは状況に応じてコンパイルする必要があります。

1.  プロジェクト名を右クリックして**ソリューション エクスプ ローラー**選択**プロパティ**を起動するコンテキスト メニューから、**プロパティ ページ** ダイアログ ボックス。

2.  選択**構成プロパティ**左側のウィンドウで、ツリー ビューから。

3.  選択**共通言語ランタイム**からサポート、**プロジェクトの既定値**右側のウィンドウの一覧。

4.  選択**共通言語ランタイム サポート (/clr)** ドロップダウン リスト ボックスから。

> [!NOTE]
>  このコンパイラ フラグを使用すると、アプリケーションでマネージド コードを使用できますが、アンマネージド コードは以前と同様にコンパイルされます。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、シングル スレッド アパートメント (STA) スレッド処理モデルを使用します。 正しく動作するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ コードは、する必要があります設定するアプリケーションのスレッド モデルを STA にエントリ ポイントに属性を適用しています。

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>WPF コンテンツのホスティング
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツは、単純なアドレス入力アプリケーションです。 それは、ユーザー名やアドレスなどを取得する複数の <xref:System.Windows.Controls.TextBox> コントロールで構成されています。 2 つあります<xref:System.Windows.Controls.Button>コントロール、 **OK**と**キャンセル**します。 ユーザーがクリックすると **[ok]**、ボタンの<xref:System.Windows.Controls.Primitives.ButtonBase.Click>からデータを収集するイベント ハンドラー、<xref:System.Windows.Controls.TextBox>を制御に対応するプロパティは、代入、およびカスタム イベントを発生させます`OnButtonClicked`します。 ユーザーがクリックすると**キャンセル**、ハンドラーが発生させるだけです`OnButtonClicked`します。 `OnButtonClicked` のイベント引数オブジェクトには、どのボタンをクリックしたかを示すブール型フィールドが含まれています。

 ホストするコード、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のハンドラーでコンテンツが実装されている、 [WM_CREATE](/windows/desktop/winmsg/wm-create)ホスト ウィンドウに通知します。

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 `GetHwnd`メソッドのサイズと位置情報および親ウィンドウ ハンドルを受け取るし、ホスト型のウィンドウ ハンドルを返します[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。

> [!NOTE]
>  `#using` 名前空間に `System::Windows::Interop` ディレクティブを使用することはできません。 使用すると、その名前空間の <xref:System.Windows.Interop.MSG> 構造体と winuser.h で宣言した MSG 構造体の間で名前の競合が発生します。 代わりに、その名前空間のコンテンツにアクセスするための完全修飾名を使用する必要があります。

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 ホストすることはできません、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツを直接アプリケーション ウィンドウ。 代わりに、まず <xref:System.Windows.Interop.HwndSource> コンテンツをラップするための [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトを作成します。 このオブジェクトをホストするように設計されたウィンドウで、基本的に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。 ホストする、<xref:System.Windows.Interop.HwndSource>親ウィンドウの子として作成することでオブジェクトを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウは、アプリケーションの一部であります。 <xref:System.Windows.Interop.HwndSource> コンストラクターのパラメーターには、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] の子ウィンドウの作成時に CreateWindow に渡される情報とほとんど同じ情報が含まれています。

 次のインスタンスを作成、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ オブジェクト。 この場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、`WPFPage` を使用して、別のクラス [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] として実装されます。 さらに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で実装することもできます。 ただし、これを行うにする必要がある別のプロジェクトを設定して、ビルド、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツとして、[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]します。 プロジェクトにその [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] への参照を追加し、その参照を使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのインスタンスを作成します。

 表示する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツへの参照を割り当てることで、子ウィンドウに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツを<xref:System.Windows.Interop.HwndSource.RootVisual%2A>のプロパティ、<xref:System.Windows.Interop.HwndSource>します。

 次のコード行は、イベント ハンドラー `WPFButtonClicked` を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの `OnButtonClicked` イベントにアタッチしています。 ユーザーがクリックしたときに、このハンドラーが呼び出されます、 **OK**または**キャンセル**ボタン。 参照してください[communicating_with_the_WPF コンテンツ](#communicating_with_the_page)このイベント ハンドラーの詳細についてはします。

 示されているコードの最後の行は、<xref:System.Windows.Interop.HwndSource> オブジェクトに関連付けられているウィンドウ ハンドル (HWND) を返します。 このハンドルは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コードから使用してホストされたウィンドウにメッセージを送信することができます。ただし、サンプルではこれはできません。 <xref:System.Windows.Interop.HwndSource> オブジェクトは、メッセージを受信するたびにイベントを発生させます。 メッセージを処理するには、<xref:System.Windows.Interop.HwndSource.AddHook%2A> メソッドを呼び出してメッセージ ハンドラーをアタッチしてから、そのハンドラーでメッセージを処理します。

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>WPF コンテンツへの参照の保持
 多くのアプリケーションでは、後で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツと通信することができます。 たとえば、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのプロパティを変更したり、場合によっては <xref:System.Windows.Interop.HwndSource> オブジェクトが異なる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストするようにしたりできます。 そのためには、<xref:System.Windows.Interop.HwndSource> オブジェクトまたは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照が必要です。 <xref:System.Windows.Interop.HwndSource> オブジェクトと関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、ウィンドウ ハンドルを破棄するまでメモリに残ります。 ただし、<xref:System.Windows.Interop.HwndSource> オブジェクトに割り当てる変数は、ウィンドウ プロシージャから戻ると同時にスコープの外に出ます。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションでこの問題を処理するためによく使用される方法は、静的変数またはグローバル変数を使用することです。 残念ながら、このような変数の種類に対してマネージド オブジェクトを割り当てることはできません。 <xref:System.Windows.Interop.HwndSource> オブジェクトに関連付けられているウィンドウ ハンドルを、グローバル変数または静的変数に割り当てることができますが、オブジェクト自体にアクセスすることはできません。

 この問題の最も簡単な解決法は、静的フィールドのセットを含むマネージド クラスを実装して、アクセスが必要なすべてのマネージド オブジェクトへの参照を保持することです。 サンプルでは、`WPFPageHost` クラスを使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツへの参照、および後でユーザーが変更する可能性があるプロパティの数の初期値を保持します。 これは、ヘッダーで定義します。

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 `GetHwnd` 関数の後半部分では、後に、`myPage` がスコープ内にある間に使用するため、対象のフィールドに値を割り当てます。

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>WPF コンテンツとの通信
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツとの通信には次の 2 種類があります。 アプリケーションから情報を受信する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ、ユーザーがクリックしたときに、 **OK**または**キャンセル**ボタン。 アプリケーションには、背景色や既定のフォント サイズなどのさまざまな [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] コンテンツのプロパティをユーザーが変更できるようにする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] があります。

 前述のように、ユーザーがいずれかのボタンをクリックすると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは `OnButtonClicked` イベントを発生させます。 アプリケーションは、これらの通知を受信するため、このイベントにハンドラーをアタッチします。 場合、 **OK**ボタンがクリックされた、ハンドラーからのユーザー情報を取得する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツし、一連の静的コントロールで表示されます。

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 ハンドラーは、カスタム イベント引数オブジェクトを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコンテンツ、`MyPageEventArgs` から受信します。 オブジェクトの`IsOK`プロパティに設定されて`true`場合、 **OK**ボタンがクリックされたと`false`場合、**キャンセル**ボタンがクリックされました。

 場合、 **OK**ボタンがクリックされた、ハンドラーへの参照を取得する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテナー クラスからのコンテンツ。 その後、関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ プロパティが保持するユーザー情報を収集し、静的コントロールを使用して親ウィンドウに情報を表示します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ データは、マネージド文字列の形式であるため、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コントロールによってマーシャリングする必要があります。 場合、**キャンセル**ボタンがクリックされ、ハンドラーは、スタティック コントロールからデータをクリアします。

 アプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] には、ユーザーが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの背景色を変更できるようにするラジオ ボタンのセット、および複数のフォント関連のプロパティが用意されています。 次の例は、アプリケーションのウィンドウ プロシージャ (WndProc)、および背景色など、各種のメッセージに対してさまざまなプロパティを設定するそのプロシージャのメッセージ処理からの抜粋です。 その他は類似しているため、示していません。 詳細とコンテキストについては、完全なサンプルを参照してください。

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 背景色を設定するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] から `hostedPage` コンテンツ (`WPFPageHost`) への参照を取得して、背景色のプロパティを適切な色に設定します。 サンプルでは、元の色、明るい緑、または明るいサーモン色の 3 つの色のオプションを使用します。 元の背景色は静的フィールドとして `WPFPageHost` クラスに格納されます。 他の 2 つの色を設定するには、新しい <xref:System.Windows.Media.SolidColorBrush> オブジェクトを作成して、<xref:System.Windows.Media.Colors> オブジェクトからコンストラクターに静的な色の値を渡します。

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>WPF ページの実装
 ホストして、使用することができます、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]実際の実装の知識がなくてもコンテンツ。 場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]別でコンテンツをパッケージ化されていた[!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]、いずれかで構築されたでした[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]言語。 以下は、このサンプルで使用する [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] の実装の簡単なチュートリアルです。 このセクションには、次のサブセクションが含まれています。

<a name="autoNestedSectionsOUTLINE2"></a>
-   [レイアウト](#page_layout)

-   [データをホスト ウィンドウに返す](#returning_data_to_window)

-   [WPF のプロパティを設定する](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>レイアウト
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]内の要素、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツから成る 5<xref:System.Windows.Controls.TextBox>制御は、関連付けられている<xref:System.Windows.Controls.Label>コントロール。名前、アドレス、市区町村、状態、および Zip です。 2 つある<xref:System.Windows.Controls.Button>コントロール、 **OK**と**キャンセル**

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは `WPFPage` クラスに実装されています。 レイアウトは、<xref:System.Windows.Controls.Grid> レイアウト要素で処理されます。 クラスは <xref:System.Windows.Controls.Grid> から継承されます。これにより、クラスは効果的に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのルート要素になります。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツのコンス トラクターは、必要な幅と高さ、およびサイズ、<xref:System.Windows.Controls.Grid>それに応じて。 セットを作成して基本的なレイアウトを定義し<xref:System.Windows.Controls.ColumnDefinition>と<xref:System.Windows.Controls.RowDefinition>オブジェクトと追加すること、<xref:System.Windows.Controls.Grid>オブジェクトの基本<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>と<xref:System.Windows.Controls.Grid.RowDefinitions%2A>コレクション、それぞれします。 これにより、5 つの行と、7 つの列のグリッドが定義され、セルの内容によって大きさが決定します。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 次に、コンストラクターは [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を <xref:System.Windows.Controls.Grid> に追加します。 最初の要素はタイトルのテキストです。これは、グリッドの 1 行目の中央に表示される <xref:System.Windows.Controls.Label> コントロールです。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 次の行には、名前の <xref:System.Windows.Controls.Label> コントロールと関連する <xref:System.Windows.Controls.TextBox> コントロールが格納されます。 ラベルとテキスト ボックスの各ペアに同じコードが使用されるため、コードはプライベート メソッドのペアに配置され、5 つのラベルとテキスト ボックスのペアすべてに使用されます。 メソッドは適切な制御を作成し、<xref:System.Windows.Controls.Grid> クラスの静的な <xref:System.Windows.Controls.Grid.SetColumn%2A> および <xref:System.Windows.Controls.Grid.SetRow%2A> メソッドを呼び出して、適切なセルにコントロールを配置します。 コントロールが作成されると、サンプルは <xref:System.Windows.Controls.UIElementCollection.Add%2A> の <xref:System.Windows.Controls.Panel.Children%2A> プロパティの <xref:System.Windows.Controls.Grid> メソッドを呼び出して、グリッドにコントロールを追加します。 残りのラベルとテキスト ボックスのペアを追加するコードは似ています。 詳細については、サンプル コードを参照してください。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 2 つのメソッドの実装は、次のとおりです。

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 最後に、サンプルは、追加、 **[ok]** と**キャンセル**] ボタンし、[イベント ハンドラーをアタッチします、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>データをホスト ウィンドウに返す
 いずれかのボタンをクリックすると、その <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントが発生します。 ホスト ウィンドウはこれらのイベントにハンドラーをアタッチして、<xref:System.Windows.Controls.TextBox> コントロールから直接データを取得します。 サンプルは、いくぶん直接的ではない方法を使用します。 処理、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>内、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ、およびカスタム イベントが発生し、`OnButtonClicked`に通知する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。 これにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツをホストに通知する前にパラメーターの検証を実行します。 ハンドラーは、<xref:System.Windows.Controls.TextBox> コントロールからテキストを取得し、パブリック プロパティに割り当てます。ここからホストは情報を取得します。

 WPFPage.h でのイベント宣言:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 WPFPage.cpp での <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラー:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>WPF のプロパティを設定する
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ホストにより、ユーザーがいくつか変更[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツのプロパティ。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 側では、これはプロパティの変更の問題にすぎません。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコンテンツ クラスの実装はいくらか複雑になります。これは、全コントロールのフォントを制御する 1 つのグローバル プロパティがないためです。 代わりに、各コントロールの適切なプロパティは、プロパティの set アクセサーで変更されます。 次の例のコードを示しています、`DefaultFontFamily`プロパティ。 プロパティを設定すると、プライベート メソッドが呼び出され、さまざまなコントロールに <xref:System.Windows.Controls.Control.FontFamily%2A> プロパティが設定されます。

 WPFPage.h から:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 WPFPage.cpp から:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.HwndSource>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)