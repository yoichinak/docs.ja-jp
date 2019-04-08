---
title: '方法: Web サービスにバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 66e91190e68d9610dd95d677edb276e117ec6abb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098580"
---
# <a name="how-to-bind-to-a-web-service"></a>方法: Web サービスにバインドする
この例では、Web サービス メソッドの呼び出しによって返されるオブジェクトにバインドする方法を示します。  
  
## <a name="example"></a>例  
 この例では、 [MSDN/TechNet Publishing System (MTPS) コンテンツ サービス](https://go.microsoft.com/fwlink/?LinkId=95677)指定されたドキュメントでサポートされる言語の一覧を取得します。  
  
 Web サービスを呼び出す前への参照を作成する必要があります。 MTPS のサービスを使用する Web 参照を作成する[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、次の手順に従います。  
  
1.  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でプロジェクトを開きます。  
  
2.  **プロジェクト** メニューのをクリックして**Web 参照の追加**します。  
  
3.  ダイアログ ボックスで、設定、 **URL**に[ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)します。  
  
4.  キーを押して**移動**し**参照の追加**します。  
  
 次に、Web サービス メソッドを呼び出して設定と、<xref:System.Windows.FrameworkElement.DataContext%2A>の適切なコントロールまたはウィンドウに返されるオブジェクト。 **GetContent** MTPS サービスのメソッドへの参照を受け取り、 **getContentRequest**オブジェクト。 そのため、次の例は、要求オブジェクトを最初に設定します。  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 後に、<xref:System.Windows.FrameworkElement.DataContext%2A>するオブジェクトのプロパティへのバインドを作成できます、設定されている、<xref:System.Windows.FrameworkElement.DataContext%2A>に設定されています。 この例で、<xref:System.Windows.FrameworkElement.DataContext%2A>に設定されている、 **getContentResponse**によって返されるオブジェクト、 **GetContent**メソッド。 次の例では、<xref:System.Windows.Controls.ItemsControl>にバインドし、表示、**ロケール**の値**availableVersionsAndLocales**の**getContentResponse**します。  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 構造体について**getContentResponse**を参照してください[コンテンツ サービス ドキュメント](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx)します。  
  
## <a name="see-also"></a>関連項目

- [データ バインディングの概要](data-binding-overview.md)
- [バインディング ソースの概要](binding-sources-overview.md)
- [XAML でデータをバインディング可能にする](how-to-make-data-available-for-binding-in-xaml.md)
