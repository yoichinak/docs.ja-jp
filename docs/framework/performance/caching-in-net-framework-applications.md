---
title: .NET Framework アプリケーションでのキャッシュ
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
ms.openlocfilehash: 14565c3e73618a4290166d89f0ae6c2c9150f3b3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586190"
---
# <a name="caching-in-net-framework-applications"></a>.NET Framework アプリケーションでのキャッシュ
キャッシュを使用すると、メモリにデータを格納して高速にアクセスできます。 アプリケーションからそのデータに再アクセスするときに、元のソースからではなく、キャッシュからデータを取得できます。 そのため、パフォーマンスとスケーラビリティが向上します。 また、データ ソースが一時的に使用できない場合でも、キャッシュのデータを使用できます。  
  
 .NET Framework には、Windows クライアントおよびサーバー アプリケーション (ASP.NET など) のパフォーマンスとスケーラビリティの改善に使用できるキャッシュ機能があります。  
  
> [!NOTE]
>  [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 以前のバージョンでは、ASP.NET は <xref:System.Web.Caching> 名前空間でメモリ内キャッシュ実装を提供していました。 以前のバージョンの .NET Framework では、キャッシュでのみ使用できますが、<xref:System.Web>名前空間と、このため ASP.NET クラスへの依存関係が必要です。 .NET Framework 4 では、Web アプリケーションと非 Web アプリケーション両方のために設計された API が <xref:System.Runtime.Caching> 名前空間に含まれています。  
  
## <a name="caching-data"></a>キャッシュされたデータ  
 情報をキャッシュするには、<xref:System.Runtime.Caching> 名前空間のクラスを使用します。 この名前空間のキャッシュ クラスには、次の機能があります。  
  
- カスタムのキャッシュ実装を作成するための基礎として機能する抽象型。  
  
- 具体的なメモリ内オブジェクト キャッシュ実装。  
  
 抽象的な基本キャッシュ クラス (<xref:System.Runtime.Caching.ObjectCache>) では、次のキャッシュ タスクを定義します。  
  
- キャッシュ エントリの作成と管理  
  
- 有効期限と削除の情報を指定します。  
  
- キャッシュ エントリの変化に応答して発生するイベントをトリガーします。  
  
 <xref:System.Runtime.Caching.MemoryCache> クラスは、<xref:System.Runtime.Caching.ObjectCache> クラスのメモリ内オブジェクト キャッシュ実装です。 ほとんどのキャッシュ タスクに <xref:System.Runtime.Caching.MemoryCache> クラスを使用できます。  
  
> [!NOTE]
>  <xref:System.Runtime.Caching.MemoryCache> クラスは、<xref:System.Web.Caching> 名前空間に定義されている ASP.NET キャッシュ オブジェクトに対してモデル化されています。 そのため、内部のキャッシュ ロジックは、旧バージョンの ASP.NET で提供されていたロジックと似ています。  
  
 WPF アプリケーションでキャッシュに使用する方法の例は、次を参照してください。[チュートリアル。WPF アプリケーションでアプリケーション データのキャッシュ](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)します。  
  
## <a name="caching-in-aspnet-applications"></a>ASP.NET アプリケーションでのキャッシュ  
 <xref:System.Runtime.Caching> 名前空間のキャッシュ クラスには、ASP.NET のデータをキャッシュするための機能があります。  
  
> [!NOTE]
>  アプリケーションが [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 以前をターゲットとしている場合は、<xref:System.Web.Caching> 名前空間で定義されているキャッシュ クラスを使用する必要があります。 詳細については、「[ASP.NET のキャッシュの概要](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100))」を参照してください。  
  
> [!NOTE]
>  新しいアプリケーションを開発する場合は、<xref:System.Runtime.Caching.MemoryCache> クラスを使用することをお勧めします。 <xref:System.Runtime.Caching> 名前空間に用意されている API は、<xref:System.Web.Caching.Cache> 名前空間に用意されている API と似ています。 そのため、旧バージョンの ASP.NET でキャッシュを使用していた場合は、なじみやすい API です。 ASP.NET アプリケーションでキャッシュを使用する方法の例は、次を参照してください。[チュートリアル。ASP.NET でのアプリケーション データのキャッシュ](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))します。  
  
### <a name="output-caching"></a>出力キャッシュ  
 アプリケーション データを手動でキャッシュするには、ASP.NET で <xref:System.Runtime.Caching.MemoryCache> クラスを使用します。 ASP.NET は出力キャッシュもサポートしており、ページ、コントロール、および HTTP 応答の生成された出力をメモリに格納します。 出力キャッシュを構成するには、ASP.NET Web ページで宣言を使用するか、Web.config ファイルの設定を使用します。 詳細については、「[outputCache Element for caching (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228124(v=vs.100))」(caching の outputCache 要素 (ASP.NET 設定スキーマ)) を参照してください。  
  
 ASP.NET では、カスタム出力キャッシュ プロバイダーを作成して、出力キャッシュを拡張できます。 カスタム プロバイダーを使用すると、キャッシュされたコンテンツを、ディスク、クラウド記憶域、分散キャッシュ エンジンなど、他の記憶域デバイスに格納できます。 カスタム出力キャッシュ プロバイダーを作成するには、<xref:System.Web.Caching.OutputCacheProvider> クラスから派生したクラスを作成し、そのカスタム出力キャッシュ プロバイダーを使用するようにアプリケーションを構成します。  
  
## <a name="caching-in-wcf-rest-services"></a>WCF REST サービスでのキャッシュ  
 WCF REST サービスで .NET Framework を使用すると、ASP.NET で使用可能な宣言型の出力キャッシュを利用できます。 このため、WCF REST サービス操作からの応答をキャッシュできます。 キャッシュ用に構成されているサービスに対してユーザーが HTTP GET 要求を送信すると、ASP.NET は、キャッシュされた応答を送り返し、サービス メソッドは呼び出されません。 キャッシュの有効期限が切れると、ユーザーが次回に HTTP GET 要求を送信したときに、サービス メソッドが呼び出され、応答が再度キャッシュされます。  
  
 .NET Framework では、条件付き HTTP GET キャッシュを実装することもできます。 REST シナリオでは、条件付き HTTP GET 要求がサービスで使用されて、[HTTP の仕様](https://go.microsoft.com/fwlink/?LinkId=165800)で説明されているように、インテリジェントな HTTP キャッシュが実装されることがよくあります。 詳細については、「[WCF WEB HTTP サービスのキャッシュ サポート](https://go.microsoft.com/fwlink/?LinkId=184598)」を参照してください。  
  
## <a name="extending-caching-in-the-net-framework"></a>.NET Framework のキャッシュを拡張する  
 .NET Framework のキャッシュは拡張できるように設計されています。 <xref:System.Runtime.Caching.ObjectCache> クラスを使用すると、カスタム キャッシュ実装を作成できます。 このクラスには、Windows フォーム、Windows Presentation Foundation(WPF)、Windows Communication Foundation (WCF) など、すべてのマネージド アプリケーションから使用できるメンバーがあります。 その目的は、異なる記憶域メカニズムを使用するキャッシュ クラスを作成するためや、キャッシュ操作をより細かく制御する場合などです。  
  
 キャッシュを拡張するには、次の方法があります。  
  
- <xref:System.Runtime.Caching.ObjectCache> クラスから派生したカスタム クラスを作成し、派生クラスでカスタム キャッシュ実装を提供します。  
  
- <xref:System.Runtime.Caching.MemoryCache> クラスから派生したクラスを作成し、派生クラスをカスタマイズまたは拡張します。 この実行方法の例については、「[Caching Application Data by Using Multiple Cache Objects in an ASP.NET Application](https://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx)」(ASP.NET アプリケーションで複数のキャッシュ オブジェクトを使用してアプリケーション データをキャッシュする) を参照してください。  
  
- <xref:System.Web.Caching.OutputCacheProvider> クラスから派生したクラスを作成し、そのカスタム出力キャッシュ プロバイダーを使用するようにアプリケーションを構成します。  
  
 詳細については、Scott Guthrie のブログのエントリ「[Extensible Output Caching with ASP.NET 4 (VS 2010 and .NET 4.0 Series)](https://go.microsoft.com/fwlink/?LinkId=185772)」(ASP.NET 4 を使用した拡張可能な出力キャッシュ (VS 2010 および .NET 4.0 シリーズ)) を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching.MemoryCache>
- [チュートリアル: WPF アプリケーションでアプリケーション データのキャッシュ](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
- [チュートリアル: ASP.NET でのアプリケーション データのキャッシュ](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))
