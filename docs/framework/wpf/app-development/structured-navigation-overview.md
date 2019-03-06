---
title: 構造化ナビゲーションの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 0a10a3f5fd07c7e3ceb7e08802f2c821b7d9a7f2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369748"
---
# <a name="structured-navigation-overview"></a>構造化ナビゲーションの概要
ホストされるコンテンツ、 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]、 <xref:System.Windows.Controls.Frame>、または<xref:System.Windows.Navigation.NavigationWindow>はパックによって識別できるページで構成されます[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]ハイパーリンクに移動するとします。 ページの構造、およびハイパーリンクで定義される移動方法を、ナビゲーション トポロジと呼びます。 このトポロジはさまざまな種類のアプリケーションに対応しますが、特にドキュメント間を移動するアプリケーションに適しています。 このようなアプリケーションでは、互いのページの情報を必要とせずに、ユーザーはページ間を移動できます。  
  
 ただし、アプリケーションによっては、移動のタイミングを理解している必要があるページを使用します。 たとえば、組織内のすべての従業員を一覧するページ ([従業員の一覧] ページ) を使用する人事アプリケーションがあるものとします。 このページでは、ハイパーリンクをクリックすることによって、新しい従業員を追加することもできます。 クリックすると、[従業員の追加] ページに移動して新しい従業員の詳細情報を収集します。次に、それを [従業員の一覧] ページに返して、新しい従業員を作成し、一覧を更新します。 このスタイルのナビゲーションは、構造化プログラミングと呼ばれる、処理を実行して値を返すメソッドの呼び出しに似ています。 そのため、このスタイルのナビゲーションを、*構造化ナビゲーション*と呼びます。  
  
 <xref:System.Windows.Controls.Page>クラスは、構造化ナビゲーションのサポートを実装しません。 代わりに、<xref:System.Windows.Navigation.PageFunction%601>クラスから派生<xref:System.Windows.Controls.Page>構造化ナビゲーションのために必要な基本コンストラクトで拡張されています。 このトピックでは、構造化ナビゲーションを使用して確立する方法を示しています。<xref:System.Windows.Navigation.PageFunction%601>します。  
  
 
  
<a name="Structured_Navigation"></a>   
## <a name="structured-navigation"></a>構造化ナビゲーション  
 構造化ナビゲーションで、あるページが別のページを呼び出す場合、以下の一部またはすべての動作が必要です。  
  
-   呼び出し元ページが、必要に応じてパラメーターを渡して、呼び出されたページに移動します。  
  
-   ユーザーが呼び出し元ページの使用を終了すると、呼び出されたページは呼び出し元ページに戻ります。このとき、次の動作が行われることがあります。  
  
    -   呼び出し元ページの終了方法 (ユーザーが [OK] または [キャンセル] をクリックしたかどうかなど) を示す状態情報を返します。  
  
    -   ユーザーから収集したデータ (新しい従業員の詳細など) を返します。  
  
-   呼び出し元ページが、呼び出されたページに戻ると、呼び出されたページはナビゲーション履歴から削除されて、呼び出されたページのインスタンスが他のインスタンスから分離されます。  
  
 これらの動作を次の図に示します。  
  
 ![呼び出し元ページと呼び出し先ページの間のフロー](./media/structurednavigationoverviewfigure1.png "StructuredNavigationOverviewFigure1")  
  
 使用してこれらの動作を実装することができます、<xref:System.Windows.Navigation.PageFunction%601>として呼び出されるページ。  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## <a name="structured-navigation-with-pagefunction"></a>PageFunction を使用した構造化ナビゲーション  
 このトピックでは、1 つに関連する構造化ナビゲーションの基本メカニズムを実装する方法を示しています。<xref:System.Windows.Navigation.PageFunction%601>します。 このサンプルで、<xref:System.Windows.Controls.Page>呼び出し、<xref:System.Windows.Navigation.PageFunction%601>を取得する、<xref:System.String>し、ユーザーからの値を返します。  
  
### <a name="creating-a-calling-page"></a>呼び出し元ページを作成する  
 呼び出すページ、<xref:System.Windows.Navigation.PageFunction%601>いずれかになります、<xref:System.Windows.Controls.Page>または<xref:System.Windows.Navigation.PageFunction%601>します。 この例では、 <xref:System.Windows.Controls.Page>、次のコードに示すようにします。  
  
 [!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### <a name="creating-a-page-function-to-call"></a>呼び出すページ関数を作成する  
 呼び出し元のページを収集して、ユーザーからデータを返す、呼び出されたページを使用できるため、<xref:System.Windows.Navigation.PageFunction%601>型引数は、呼び出されたページが返される値の型を指定するジェネリック クラスとして実装されます。 次のコードは、呼び出されたは、最初の実装を使用して、ページ、 <xref:System.Windows.Navigation.PageFunction%601>、返された、 <xref:System.String>。  
  
 [!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 宣言を<xref:System.Windows.Navigation.PageFunction%601>の宣言に似ていますが、<xref:System.Windows.Controls.Page>に型引数を追加します。 コード例に示されているように、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップ (`x:TypeArguments` 属性を使用) と分離コード (標準のジェネリック型引数構文を使用) の両方で型引数が指定されています。  
  
 型引数として [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] クラスのみを使用する必要はありません。 A<xref:System.Windows.Navigation.PageFunction%601>カスタム型として抽象化は、ドメイン固有のデータを収集するために呼び出すことができます。 次のコードに対して型引数としてカスタムの型を使用する方法を示しています、<xref:System.Windows.Navigation.PageFunction%601>します。  
  
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
  
 型引数、<xref:System.Windows.Navigation.PageFunction%601>については、次のセクションで説明する呼び出し元ページと、呼び出されるページ間の通信の基盤を提供します。  
  
 ご覧のとおり、型の宣言で識別されるよう、<xref:System.Windows.Navigation.PageFunction%601>からデータを返すときに重要な役割を果たします、<xref:System.Windows.Navigation.PageFunction%601>呼び出し元ページにします。  
  
### <a name="calling-a-pagefunction-and-passing-parameters"></a>PageFunction を呼び出してパラメーターを渡す  
 ページを呼び出すには、呼び出し元ページする必要があります、呼び出されたページをインスタンス化しを使用して、<xref:System.Windows.Navigation.NavigationService.Navigate%2A>メソッド。 これにより、呼び出し元ページは、呼び出されるページで収集されるデータの既定値など、呼び出されるページに初期データを渡すことができます。  
  
 既定以外のコンストラクターを使用して呼び出されたページが、呼び出し元ページからパラメーターを受け取るコードを次に示します。  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 次のコードは呼び出し元のページ処理、<xref:System.Windows.Documents.Hyperlink.Click>のイベント、<xref:System.Windows.Documents.Hyperlink>呼び出されたページをインスタンス化し、初期の文字列値を渡します。  
  
 [!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 呼び出されるページにパラメーターを渡す必要はありません。 代わりに、以下を実行できます。  
  
-   呼び出し元ページの場合:  
  
    1.  呼び出されたインスタンス化<xref:System.Windows.Navigation.PageFunction%601>既定コンス トラクターを使用します。  
  
    2.  内のパラメーターを格納<xref:System.Windows.Application.Properties%2A>します。  
  
    3.  呼び出されたに移動します<xref:System.Windows.Navigation.PageFunction%601>します。  
  
-   呼び出されたから<xref:System.Windows.Navigation.PageFunction%601>:  
  
    -   取得しに格納されているパラメーターを使用して<xref:System.Windows.Application.Properties%2A>します。  
  
 しかし、この後の説明にもあるように、コードを使用して呼び出されたページをインスタンス化して、そのページに移動して、呼び出されたページから返されるデータを収集する必要が依然としてあります。 このため、<xref:System.Windows.Navigation.PageFunction%601>に移動するそれ以外の動作を保持する必要がある、次回、 <xref:System.Windows.Navigation.PageFunction%601>、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]をインスタンス化、<xref:System.Windows.Navigation.PageFunction%601>既定コンス トラクターを使用します。  
  
 ただし、呼び出されたページが戻る前に、呼び出し元ページが取得できるデータを返す必要があります。  
  
### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>タスクから呼び出し元ページにタスク結果とタスク データを返す  
 ユーザーが呼び出されたページの使用を終了すると (この例では、[OK] または [キャンセル] をクリックすることで表されます)、呼び出されたページは戻る必要があります。 呼び出し元ページは、呼び出されたページを使用してユーザーからデータを収集したため、呼び出し元ページには 2 種類の情報が必要です。  
  
1.  ユーザーが呼び出されたページをキャンセルしたかどうか (この例では、[OK] と [キャンセル] のどちらをクリックしたかで表されます)。 これによって、呼び出し元ページは、ユーザーから収集したデータを処理するかどうかを判断します。  
  
2.  ユーザーが提供したデータ。  
  
 情報を返すことを<xref:System.Windows.Navigation.PageFunction%601>実装、<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>メソッド。 その呼び出し方法を次のコードに示します。  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 この例では、ユーザーが [キャンセル] をクリックすると、呼び出し元ページに値 `null` が返されます。 ユーザーが [OK] をクリックすると、ユーザーによって指定された文字列値が返されます。 <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> `protected virtual`に呼び出し元のページにデータを返すメソッド。 ジェネリックのインスタンスにパッケージ化する必要があるデータ<xref:System.Windows.Navigation.ReturnEventArgs%601>型、型引数の型を指定する値を<xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A>を返します。 宣言するときに、この方法で、 <xref:System.Windows.Navigation.PageFunction%601> 、特定の型引数であることは、<xref:System.Windows.Navigation.PageFunction%601>は型引数で指定された型のインスタンスを返します。 この例で、型引数、およびその結果、戻り値は型の<xref:System.String>します。  
  
 ときに<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>を呼び出すと、呼び出し元ページはなんらかの方法の戻り値を受け取る、<xref:System.Windows.Navigation.PageFunction%601>します。 このため、<xref:System.Windows.Navigation.PageFunction%601>実装、<xref:System.Windows.Navigation.PageFunction%601.Return>イベントを処理するためにページを呼び出すことです。 ときに<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>が呼び出され、<xref:System.Windows.Navigation.PageFunction%601.Return>が発生する、呼び出し元ページに登録できますので<xref:System.Windows.Navigation.PageFunction%601.Return>通知を受信します。  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### <a name="removing-task-pages-when-a-task-completes"></a>タスク完了時にタスク ページを削除する  
 呼び出されたページが戻り、呼び出されたページをユーザーが取り消さなかった場合、呼び出し元ページでは、ユーザーから提供されたデータだけでなく、呼び出されたページから返されたデータも処理します。 このような方法で行われるデータ取得は、通常は分離されたアクティビティです。呼び出されたページが戻ると、呼び出し元ページでは、さらにデータをキャプチャするために、新しい呼び出し元ページを作成し、そこに移動する必要があります。  
  
 ただし、呼び出されたページが履歴から削除されない限り、ユーザーは呼び出し元ページの前のインスタンスに戻ることができます。 かどうかを<xref:System.Windows.Navigation.PageFunction%601>に保持されますが、journal はによって決定されます、<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>プロパティ。 ページ関数を自動的には既定では、削除<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>呼び出されるため<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>に設定されている`true`します。 ページ関数を後のナビゲーション履歴に保持する<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>を呼び出すと、設定<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>に`false`します。  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## <a name="other-types-of-structured-navigation"></a>他の種類の構造化ナビゲーション  
 このトピックの最も基本的な使用方法を示します、<xref:System.Windows.Navigation.PageFunction%601>呼び出しと戻りをサポートするためにナビゲーション構造化します。 これに基づいて、より複雑な構造化ナビゲーションを作成できます。  
  
 たとえば、呼び出し元ページがユーザーから十分なデータを収集したり、タスクを実行するには、複数のページが必要な場合があります。 複数のページを使用する場合、これを "ウィザード" と呼びます。  
  
 また、構造化ナビゲーションに基づいて効率的な操作を実行する複雑なナビゲーション トポロジを使用するアプリケーションもあります。 詳細については、「[ナビゲーション トポロジの概要](navigation-topologies-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [ナビゲーション トポロジの概要](navigation-topologies-overview.md)
