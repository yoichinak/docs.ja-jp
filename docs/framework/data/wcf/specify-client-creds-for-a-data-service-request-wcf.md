---
title: '方法: データ サービス クライアントの資格情報要求 (WCF Data Services) を指定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: ca2ed1fcf113e06535c8900e5836eb64f9b23958
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59518137"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>方法: データ サービス クライアントの資格情報要求 (WCF Data Services) を指定します。
既定では、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスに要求を送信する際、クライアント ライブラリから資格情報は提供されません。 ただし、<xref:System.Net.NetworkCredential> の <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> プロパティに <xref:System.Data.Services.Client.DataServiceContext> を設定することで、データ サービスへの要求を認証するために資格情報を送信するように指定できます。 詳細については、「 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。 このトピックの例では、データ サービスのデータを要求する際に [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントで使用する資格情報を明示的に提供する方法を示します。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスを作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。 使用することも、 [Northwind サンプル データ サービス](https://go.microsoft.com/fwlink/?LinkId=187426)で公開されている、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web サイト。 このサンプル データ サービスは読み取り専用と変更を保存しようとしてエラーが返されます。 サンプル データ サービスでは、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web サイトは、匿名認証を許可します。  
  
## <a name="example"></a>例  
 次の例は、Windows Presentation Framework アプリケーションのメイン ページである Extensible Application Markup Language (XAML) ファイルの分離コード ページです。 この例では、`LoginWindow` インスタンスを表示してユーザーから認証資格情報を収集し、データ サービスへの要求を行うときにこれらの資格情報を使用します。  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>例  
 次の XAML は、WPF アプリケーションのメイン ページを定義します。  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>例  
 次の例は、データ サービスへの要求を行う前にユーザーから認証資格情報を収集するために使用するウィンドウの分離コード ページからの抜粋です。  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>例  
 次の XAML は、WPF アプリケーションのログインを定義します。  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 このトピックの例には、以下のセキュリティに関する注意点があります。  
  
-   このサンプルで指定した資格情報が機能することを確認するには、Northwind データ サービスで匿名アクセス以外の認証方式を使用する必要があります。 そうしない場合、データ サービスをホストする Web サイトが資格情報を要求しません。  
  
-   ユーザー資格情報は実行時にのみ要求し、キャッシュしないようにする必要があります。 資格情報は常に安全に格納する必要があります。  
  
-   基本認証およびダイジェスト認証で送信されるデータは暗号化されないため、敵対者がデータを見ることができます。 また、基本認証の資格情報 (ユーザー名とパスワード) はクリア テキストで送信されるので、傍受される可能性があります。  
  
 詳細については、「 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
