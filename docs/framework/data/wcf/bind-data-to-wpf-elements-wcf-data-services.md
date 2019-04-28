---
title: '方法: Windows Presentation Foundation 要素 (WCF Data Services) にデータをバインドします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: 1deb5bcc29e43720929951764d1fcfeee8e89f8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793407"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>方法: Windows Presentation Foundation 要素 (WCF Data Services) にデータをバインドします。
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]など、Windows Presentation Foundation (WPF) 要素をバインドすることができます、<xref:System.Windows.Controls.ListBox>または<xref:System.Windows.Controls.ComboBox>のインスタンスに<xref:System.Data.Services.Client.DataServiceCollection%601>、維持するためにコントロールによって生成されるイベントを処理する、<xref:System.Data.Services.Client.DataServiceContext>変更と同期コントロール内のデータに行われます。 詳細については、次を参照してください。[データ コントロールをバインド](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)します。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスを作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。  
  
## <a name="example"></a>例  
 次の例は、WPF で `SalesOrders` ウィンドウを定義する XAML (Extensible Application Markup Language) の分離コード ページからの抜粋です。 ウィンドウが読み込まれると、国別にフィルターされた顧客を返すクエリの結果に基づいて <xref:System.Data.Services.Client.DataServiceCollection%601> が作成されます。 このページングされた結果のすべてのページが関連する注文と一緒に読み込まれ、WPF ウィンドウのルート レイアウト コントロールである <xref:System.Windows.FrameworkElement.DataContext%2A> の <xref:System.Windows.Controls.StackPanel> プロパティにバインドされます。 詳細については、次を参照してください。[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)します。  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>例  
 次の XAML は、前の例の WPF の `SalesOrders` ウィンドウを定義します。  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>例  
 次の例は、WPF で `SalesOrders` ウィンドウを定義する XAML (Extensible Application Markup Language) の分離コード ページからの抜粋です。 ウィンドウが読み込まれると、国別にフィルターされた顧客を関連するオブジェクトと一緒に返すクエリの結果に基づいて <xref:System.Data.Services.Client.DataServiceCollection%601> が作成されます。 この結果は、WPF ウィンドウのルート レイアウト コントロールである <xref:System.Windows.FrameworkElement.DataContext%2A> の <xref:System.Windows.Controls.StackPanel> プロパティにバインドされます。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>例  
 次の XAML は、前の例の WPF の `SalesOrders` ウィンドウを定義します。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
