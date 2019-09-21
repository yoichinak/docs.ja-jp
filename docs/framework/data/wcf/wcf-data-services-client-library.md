---
title: WCF Data Services クライアント ライブラリ
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 545442b0086361c8ce8c0482801afc10b1fee96e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779685"
---
# <a name="wcf-data-services-client-library"></a>WCF Data Services クライアント ライブラリ
HTTP 要求を送信し、データ サービスが返す [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードを処理できるのであれば、どのようなアプリケーションでも [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのデータ サービスと対話できます。 この相互運用性によって、広範な Web 対応アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービスにアクセスすることが可能になります。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]には、.NET Framework または Silverlight ベースのアプリケーションからフィード[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]を使用するときに、より高度なプログラミングエクスペリエンスを提供するクライアントライブラリが含まれています。  
  
 クライアント ライブラリの 2 つの主要なクラスは、<xref:System.Data.Services.Client.DataServiceContext> クラスと <xref:System.Data.Services.Client.DataServiceQuery%601> クラスです。 <xref:System.Data.Services.Client.DataServiceContext> クラスは、特定のデータ サービスに対してサポートされている操作をカプセル化します。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスはステートレスですが、コンテキストはステートレスではありません。 そのため、 <xref:System.Data.Services.Client.DataServiceContext>クラスを使用して、変更管理などの機能をサポートするために、データサービスとのやり取りの間にクライアントの状態を維持することができます。 このクラスは、ID の管理と変更の追跡も行います。 <xref:System.Data.Services.Client.DataServiceQuery%601> クラスは、特定のエンティティ セットに対するクエリを表します。  
  
 このセクションでは、クライアント ライブラリを使用して .NET Framework クライアント アプリケーションからデータにアクセスしてデータを変更する方法について説明します。 Silverlight ベースのアプリケーションで[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]クライアントライブラリを使用する方法の詳細については、「 [WCF Data Services (silverlight)](https://go.microsoft.com/fwlink/?LinkId=186016)」を参照してください。 他の種類のアプリケーションで[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードを使用できるようにするその他のクライアントライブラリも用意されています。 詳細については、 [ODATA SDK](https://go.microsoft.com/fwlink/?LinkID=185796)を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データ サービス クライアント ライブラリの生成](generating-the-data-service-client-library-wcf-data-services.md)  
 フィードに[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]基づいてクライアントライブラリとクライアントデータサービスクラスを生成する方法について説明します。  
  
 [データ サービスに対するクエリ](querying-the-data-service-wcf-data-services.md)  
 クライアント ライブラリを使用して .NET Framework ベースのアプリケーションからデータ サービスを照会する方法について説明します。  
  
 [遅延コンテンツの読み込み](loading-deferred-content-wcf-data-services.md)  
 最初のクエリ応答に含まれない追加のコンテンツを読み込む方法について説明します。  
  
 [データ サービスの更新](updating-the-data-service-wcf-data-services.md)  
 クライアント ライブラリを使用してエンティティおよびリレーションシップを作成、変更、および削除する方法について説明します。  
  
 [非同期操作](asynchronous-operations-wcf-data-services.md)  
 非同期でデータ サービスを操作するためにクライアント ライブラリで提供される機能について説明します。  
  
 [バッチ処理](batching-operations-wcf-data-services.md)  
 クライアント ライブラリを使用して複数の要求を 1 つのバッチでデータ サービスに送信する方法について説明します。  
  
 [コントロールへのデータのバインド](binding-data-to-controls-wcf-data-services.md)  
 データサービスによって返される[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードにコントロールをバインドする方法について説明します。  
  
 [サービス操作の呼び出し](calling-service-operations-wcf-data-services.md)  
 クライアント ライブラリを使用してサービス操作を呼び出す方法について説明します。  
  
 [データ サービス コンテキストの管理](managing-the-data-service-context-wcf-data-services.md)  
 クライアント ライブラリの動作を管理するオプションについて説明します。  
  
 [バイナリ データの操作](working-with-binary-data-wcf-data-services.md)  
 データ サービスによってデータ ストリームとして返されるバイナリ データにアクセスしてバイナリ データを変更する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services の定義](defining-wcf-data-services.md)
- [はじめに](getting-started-with-wcf-data-services.md)
