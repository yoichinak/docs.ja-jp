---
title: 構造化ナビゲーションの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 8760c847d9e73fdff9f10f0dfa55a6c674021667
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364178"
---
# <a name="structured-navigation-overview"></a>構造化ナビゲーションの概要

、、また[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] は<xref:System.Windows.Navigation.NavigationWindow>でホストできるコンテンツは、パックによって識別され、ハイパーリンクによって移動できるページで構成されます。 <xref:System.Windows.Controls.Frame> [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] ページの構造、およびハイパーリンクで定義される移動方法を、ナビゲーション トポロジと呼びます。 このトポロジはさまざまな種類のアプリケーションに対応しますが、特にドキュメント間を移動するアプリケーションに適しています。 このようなアプリケーションでは、互いのページの情報を必要とせずに、ユーザーはページ間を移動できます。

ただし、アプリケーションによっては、移動のタイミングを理解している必要があるページを使用します。 たとえば、組織内のすべての従業員を一覧するページ ([従業員の一覧] ページ) を使用する人事アプリケーションがあるものとします。 このページでは、ハイパーリンクをクリックすることによって、新しい従業員を追加することもできます。 クリックすると、[従業員の追加] ページに移動して新しい従業員の詳細情報を収集します。次に、それを [従業員の一覧] ページに返して、新しい従業員を作成し、一覧を更新します。 このスタイルのナビゲーションは、構造化プログラミングと呼ばれる、処理を実行して値を返すメソッドの呼び出しに似ています。 そのため、このスタイルのナビゲーションを、*構造化ナビゲーション*と呼びます。

クラス<xref:System.Windows.Controls.Page>は、構造化ナビゲーションのサポートを実装していません。 代わりに、クラス<xref:System.Windows.Navigation.PageFunction%601>はから<xref:System.Windows.Controls.Page>派生し、構造化ナビゲーションに必要な基本構成体を使用して拡張します。 このトピックでは、を使用して<xref:System.Windows.Navigation.PageFunction%601>構造化ナビゲーションを確立する方法について説明します。

<a name="Structured_Navigation"></a>

## <a name="structured-navigation"></a>構造化ナビゲーション

構造化ナビゲーションで、あるページが別のページを呼び出す場合、以下の一部またはすべての動作が必要です。

- 呼び出し元ページが、必要に応じてパラメーターを渡して、呼び出されたページに移動します。

- ユーザーが呼び出し元ページの使用を終了すると、呼び出されたページは呼び出し元ページに戻ります。このとき、次の動作が行われることがあります。

  - 呼び出し元ページの終了方法 (ユーザーが [OK] または [キャンセル] をクリックしたかどうかなど) を示す状態情報を返します。

  - ユーザーから収集したデータ (新しい従業員の詳細など) を返します。

- 呼び出し元ページが、呼び出されたページに戻ると、呼び出されたページはナビゲーション履歴から削除されて、呼び出されたページのインスタンスが他のインスタンスから分離されます。

これらの動作を次の図に示します。

![スクリーンショットは、呼び出し元ページと呼び出し先ページの間のフローを示しています。](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)

これらの動作を実装するには<xref:System.Windows.Navigation.PageFunction%601> 、を呼び出されたページとしてを使用します。

<a name="Structured_Navigation_with_PageFunction"></a>

## <a name="structured-navigation-with-pagefunction"></a>PageFunction を使用した構造化ナビゲーション

このトピックでは、単一<xref:System.Windows.Navigation.PageFunction%601>のを含む構造化ナビゲーションの基本的なメカニズムを実装する方法について説明します。 このサンプルでは、 <xref:System.Windows.Controls.Page>はを<xref:System.Windows.Navigation.PageFunction%601>呼び出してユーザー <xref:System.String>から値を取得し、それを返します。

### <a name="creating-a-calling-page"></a>呼び出し元ページを作成する

を<xref:System.Windows.Navigation.PageFunction%601>呼び出すページに<xref:System.Windows.Controls.Page>は、また<xref:System.Windows.Navigation.PageFunction%601>はのいずれかを指定できます。 この例では、次の<xref:System.Windows.Controls.Page>コードに示すように、です。

[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]

[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]

### <a name="creating-a-page-function-to-call"></a>呼び出すページ関数を作成する

呼び出し元ページは、呼び出されたページを使用してユーザーからデータを収集<xref:System.Windows.Navigation.PageFunction%601>して返すことができるため、は、呼び出されたページが返す値の型を指定する型引数を持つジェネリッククラスとして実装されます。 次のコードは、を使用して、呼び出されたページ<xref:System.Windows.Navigation.PageFunction%601>の初期実装を<xref:System.String>示しています。これはを返します。

[!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]

[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]

の<xref:System.Windows.Navigation.PageFunction%601>宣言は、 <xref:System.Windows.Controls.Page>型引数を追加したの宣言に似ています。 コード例に示されているように、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップ (`x:TypeArguments` 属性を使用) と分離コード (標準のジェネリック型引数構文を使用) の両方で型引数が指定されています。

.NET Framework クラスのみを型引数として使用する必要はありません。 を<xref:System.Windows.Navigation.PageFunction%601>呼び出すことにより、カスタム型として抽象化されたドメイン固有のデータを収集できます。 次のコードは、 <xref:System.Windows.Navigation.PageFunction%601>の型引数としてカスタム型を使用する方法を示しています。

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]

[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]

の型引数<xref:System.Windows.Navigation.PageFunction%601>は、次のセクションで説明されている呼び出し元ページと呼び出し先ページの間の通信の基礎を提供します。

ご覧のように、の<xref:System.Windows.Navigation.PageFunction%601>宣言で識別される型は、 <xref:System.Windows.Navigation.PageFunction%601>から呼び出し元のページにデータを返す際に重要な役割を果たします。

### <a name="calling-a-pagefunction-and-passing-parameters"></a>PageFunction を呼び出してパラメーターを渡す

ページを呼び出すには、呼び出し元ページが呼び出されたページをインスタンス化し、 <xref:System.Windows.Navigation.NavigationService.Navigate%2A>メソッドを使用してそのページに移動する必要があります。 これにより、呼び出し元ページは、呼び出されるページで収集されるデータの既定値など、呼び出されるページに初期データを渡すことができます。

次のコードは、呼び出し元ページからパラメーターを受け取る、パラメーターなしのコンストラクターを持つ呼び出されたページを示しています。

[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]

次のコードは、の<xref:System.Windows.Documents.Hyperlink.Click>イベントを処理する呼び出し元ページを示しています。このページでは、 <xref:System.Windows.Documents.Hyperlink>呼び出されたページをインスタンス化し、それに最初の文字列値を渡します。

[!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]

呼び出されるページにパラメーターを渡す必要はありません。 代わりに、以下を実行できます。

- 呼び出し元ページの場合:

  1. パラメーターなしの<xref:System.Windows.Navigation.PageFunction%601>コンストラクターを使用して、呼び出されたをインスタンス化します。

  2. に<xref:System.Windows.Application.Properties%2A>パラメーターを格納します。

  3. 呼び出さ<xref:System.Windows.Navigation.PageFunction%601>れたに移動します。

- 呼び出され<xref:System.Windows.Navigation.PageFunction%601>たから:

  - に<xref:System.Windows.Application.Properties%2A>格納されているパラメーターを取得して使用します。

しかし、この後の説明にもあるように、コードを使用して呼び出されたページをインスタンス化して、そのページに移動して、呼び出されたページから返されるデータを収集する必要が依然としてあります。 この<xref:System.Windows.Navigation.PageFunction%601>ため、を有効にする必要があります。それ以外の場合は、次<xref:System.Windows.Navigation.PageFunction%601>にに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]移動する<xref:System.Windows.Navigation.PageFunction%601>ときに、パラメーターなしのコンストラクターを使用してをインスタンス化します。

ただし、呼び出されたページが戻る前に、呼び出し元ページが取得できるデータを返す必要があります。

### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>タスクから呼び出し元ページにタスク結果とタスク データを返す

ユーザーが呼び出されたページの使用を終了すると (この例では、[OK] または [キャンセル] をクリックすることで表されます)、呼び出されたページは戻る必要があります。 呼び出し元ページは、呼び出されたページを使用してユーザーからデータを収集したため、呼び出し元ページには 2 種類の情報が必要です。

1. ユーザーが呼び出されたページをキャンセルしたかどうか (この例では、[OK] と [キャンセル] のどちらをクリックしたかで表されます)。 これによって、呼び出し元ページは、ユーザーから収集したデータを処理するかどうかを判断します。

2. ユーザーが提供したデータ。

情報を返すに<xref:System.Windows.Navigation.PageFunction%601>は、 <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>メソッドを実装します。 その呼び出し方法を次のコードに示します。

[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]

この例では、ユーザーが [キャンセル] をクリックすると、呼び出し元ページに値 `null` が返されます。 ユーザーが [OK] をクリックすると、ユーザーによって指定された文字列値が返されます。 <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>は、呼び出し元のページにデータを返すために呼び出すメソッドです。`protected virtual` データは、が<xref:System.Windows.Navigation.ReturnEventArgs%601> <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A>返す値の型を指定する型引数を持つジェネリック型のインスタンスにパッケージ化する必要があります。 このようにして、特定の<xref:System.Windows.Navigation.PageFunction%601>型引数を持つを宣言するときに、型<xref:System.Windows.Navigation.PageFunction%601>引数によって指定された型のインスタンスがによって返されることを示します。 この例では、型引数と、戻り値の型<xref:System.String>はです。

が<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>呼び出された場合、呼び出し元ページは、 <xref:System.Windows.Navigation.PageFunction%601>の戻り値を受け取るための何らかの方法を必要とします。 このため、は<xref:System.Windows.Navigation.PageFunction%601> 、処理<xref:System.Windows.Navigation.PageFunction%601.Return>するページを呼び出すためのイベントを実装します。 が<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>呼び出されると<xref:System.Windows.Navigation.PageFunction%601.Return> 、が発生します。そのため、呼び出し<xref:System.Windows.Navigation.PageFunction%601.Return>元ページは、通知を受信するためにに登録できます。

[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]

### <a name="removing-task-pages-when-a-task-completes"></a>タスク完了時にタスク ページを削除する

呼び出されたページが戻り、呼び出されたページをユーザーが取り消さなかった場合、呼び出し元ページでは、ユーザーから提供されたデータだけでなく、呼び出されたページから返されたデータも処理します。 このような方法で行われるデータ取得は、通常は分離されたアクティビティです。呼び出されたページが戻ると、呼び出し元ページでは、さらにデータをキャプチャするために、新しい呼び出し元ページを作成し、そこに移動する必要があります。

ただし、呼び出されたページが履歴から削除されない限り、ユーザーは呼び出し元ページの前のインスタンスに戻ることができます。 が履歴に保持されるかどうかは、 <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>プロパティによって決まります。 <xref:System.Windows.Navigation.PageFunction%601> 既定では、がに<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> `true`設定されているため<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>にが呼び出されると、ページ関数が自動的に削除されます。 が呼び出された後<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>にナビゲーション履歴にページ関数を保持するには、をに`false`設定<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>します。

<a name="Other_Types_of_Structured_Navigation"></a>

## <a name="other-types-of-structured-navigation"></a>他の種類の構造化ナビゲーション

このトピックでは、を使用して<xref:System.Windows.Navigation.PageFunction%601> 、構造化ナビゲーションの呼び出し/戻りをサポートする最も基本的な使用方法について説明します。 これに基づいて、より複雑な構造化ナビゲーションを作成できます。

たとえば、呼び出し元ページがユーザーから十分なデータを収集したり、タスクを実行するには、複数のページが必要な場合があります。 複数のページを使用する場合、これを "ウィザード" と呼びます。

また、構造化ナビゲーションに基づいて効率的な操作を実行する複雑なナビゲーション トポロジを使用するアプリケーションもあります。 詳細については、「[ナビゲーション トポロジの概要](navigation-topologies-overview.md)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [ナビゲーション トポロジの概要](navigation-topologies-overview.md)
