---
title: 非同期操作 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: bb62b9ad214e5e268c3905df486f5914437b36d3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780523"
---
# <a name="asynchronous-operations-wcf-data-services"></a>非同期操作 (WCF Data Services)
Web アプリケーションは、内部ネットワーク内で実行するアプリケーションより長い、クライアントとサーバーとの間の待機時間に対応する必要があります。 Web を介して <xref:System.Data.Services.Client.DataServiceContext> サーバーにアクセスする場合、アプリケーションのパフォーマンスとユーザー エクスペリエンスを最適化するために <xref:System.Data.Services.Client.DataServiceQuery%601> クラスおよび [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クラスの非同期メソッドを使用することをお勧めします。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] サーバーでは、HTTP 要求は非同期として処理されますが、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリの一部のメソッドは同期であり、要求と応答のやり取りがすべて完了するまで待ってから実行を継続します。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリの非同期メソッドは、このやり取りの完了を待たず、アプリケーションはユーザー インターフェイスの応答性を維持できます。  
  
 非同期操作を実行するには、 <xref:System.Data.Services.Client.DataServiceContext>クラスと<xref:System.Data.Services.Client.DataServiceQuery%601>クラスで、それぞれ*Begin*および*End*で始まるメソッドのペアを使用します。 *Begin*メソッドは、操作の完了時にサービスが呼び出すデリゲートを登録します。 *終了*メソッドは、完了した操作からのコールバックを処理するために登録されているデリゲートで呼び出す必要があります。 非同期操作を完了するために*End*メソッドを呼び出す場合は、操作を開始する<xref:System.Data.Services.Client.DataServiceQuery%601>ときに使用したのと同じインスタンスまたは<xref:System.Data.Services.Client.DataServiceContext>インスタンスから実行する必要があります。 各*Begin*メソッドは、 `state`状態オブジェクトをコールバックに渡すことができるパラメーターを受け取ります。 この状態オブジェクトは、 <xref:System.IAsyncResult>コールバックで提供されたから取得され、対応する*End*メソッドを呼び出して非同期操作を完了するために使用されます。 たとえば、<xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスで `state` メソッドを呼び出すときにインスタンスを <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> パラメーターとして指定した場合、同じ <xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスが <xref:System.IAsyncResult> によって返されます。 この <xref:System.Data.Services.Client.DataServiceQuery%601> のインスタンスは、<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> メソッドを呼び出してクエリ操作を完了するために使用されます。 詳細については、「[方法 :非同期データサービスクエリ](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)を実行します。  
  
> [!NOTE]
> Silverlight 用の .NET Framework で提供されるクライアント ライブラリでは、非同期操作だけがサポートされます。 詳細については、「 [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)」を参照してください。  
  
 .NET Framework クライアント ライブラリは、以下の非同期操作をサポートします。  
  
|操作|メソッド|  
|---------------|-------------|  
|<xref:System.Data.Services.Client.DataServiceQuery%601> の実行。|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> からのクエリの実行。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> からのバッチ クエリの実行。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> への関連エンティティの読み込み。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|オブジェクトに対する変更の <xref:System.Data.Services.Client.DataServiceContext> への保存。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>非同期操作のスレッドに関する考慮事項  
 マルチスレッドアプリケーションでは、非同期操作のコールバックとして登録されたデリゲートは、最初の要求を作成する*Begin*メソッドの呼び出しに使用されたのと同じスレッドで必ずしも呼び出されるとは限りません。 特定のスレッドでコールバックを呼び出す必要があるアプリケーションでは、応答を処理する*End*メソッドの実行を目的のスレッドに明示的にマーシャリングする必要があります。 たとえば、Windows Presentation Foundation (WPF) ベースのアプリケーションおよび Silverlight ベースのアプリケーションでは、<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> オブジェクトで <xref:System.Windows.Threading.Dispatcher> メソッドを使用して応答を UI スレッドにマーシャリングする必要があります。 詳細については、「[データサービスのクエリ (WCF Data Services/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95))」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)
