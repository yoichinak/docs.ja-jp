---
title: '方法: Windows Presentation Foundation 要素にデータをバインドする (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: 44f3361aa56d9f15e62852000accd0b4d4d8eb43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791133"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>方法: Windows Presentation Foundation 要素にデータをバインドする (WCF Data Services)
を[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]使用すると、 <xref:System.Windows.Controls.ListBox>や<xref:System.Windows.Controls.ComboBox>などの Windows Presentation Foundation (WPF) 要素をの<xref:System.Data.Services.Client.DataServiceCollection%601>インスタンスにバインドできます。 <xref:System.Data.Services.Client.DataServiceContext>これは、コントロールによって発生したイベントを処理して、変更との同期を維持します。コントロール内のデータに対して作成されます。 詳細については、「[コントロールへのデータのバインド](binding-data-to-controls-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアントデータクラスは、 [WCF Data Services のクイックスタート](quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## <a name="example"></a>例  
 次の例は、WPF で `SalesOrders` ウィンドウを定義する XAML (Extensible Application Markup Language) の分離コード ページからの抜粋です。 ウィンドウが読み込ま<xref:System.Data.Services.Client.DataServiceCollection%601>れると、国/地域によってフィルター処理された顧客を返すクエリの結果に基づいてが作成されます。 このページングされた結果のすべてのページが関連する注文と一緒に読み込まれ、WPF ウィンドウのルート レイアウト コントロールである <xref:System.Windows.FrameworkElement.DataContext%2A> の <xref:System.Windows.Controls.StackPanel> プロパティにバインドされます。 詳細については、「[遅延コンテンツの読み込み](loading-deferred-content-wcf-data-services.md)」を参照してください。  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>例  
 次の XAML は、前の例の WPF の `SalesOrders` ウィンドウを定義します。  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>例  
 次の例は、WPF で `SalesOrders` ウィンドウを定義する XAML (Extensible Application Markup Language) の分離コード ページからの抜粋です。 ウィンドウが読み込ま<xref:System.Data.Services.Client.DataServiceCollection%601>れると、国/地域でフィルター処理された関連オブジェクトを持つ顧客を返すクエリの結果に基づいてが作成されます。 この結果は、WPF ウィンドウのルート レイアウト コントロールである <xref:System.Windows.FrameworkElement.DataContext%2A> の <xref:System.Windows.Controls.StackPanel> プロパティにバインドされます。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>例  
 次の XAML は、前の例の WPF の `SalesOrders` ウィンドウを定義します。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
