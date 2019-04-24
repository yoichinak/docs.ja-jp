---
title: WCF サービスの構成
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 81727adbf985986a71cc9f9e2d42a1de0cb1fd76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156508"
---
# <a name="configuring-wcf-services"></a>WCF サービスの構成

サービス コントラクトの設計、実装が終われば、サービスを構成できる状態になります。 クライアント側から見たサービスの動作は、ここで定義、カスタマイズします。サービスと通信するためのアドレス、メッセージの送受信に使うトランスポートやエンコーディング、必要なセキュリティ型などを指定できます。  
  
 定義やカスタマイズは、コード内で強制的に (簡単には変更できないような形で) 行う方法と、構成ファイルに記述して行う方法があります。エンドポイントのアドレス、実際に使うトランスポート、セキュリティ スキーマなど、サービスに関するさまざまな事項を定義、カスタマイズできます。 実際には、構成ファイルの記述は、大規模な WCF アプリケーションのプログラミングの一部です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)  
 以降で[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]WCF が付属して新しい既定の構成モデルを WCF 構成の要件を簡略化します。 特定のサービスの WCF 構成を指定しない場合、ランタイムでサービスの既定のエンドポイント、バインディング、および動作を自動的に構成します。  
  
 [構成ファイルを使用してサービスを構成する方法](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Windows Communication Foundation (WCF) サービスが構成可能なを使用して、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]テクノロジの構成。 ほとんどの場合、XML 要素は、WCF サービスをホストするインターネット インフォメーション サービス (IIS) サイトの Web.config ファイルに追加されます。 この要素によって、コンピューターごとにエンドポイント アドレス (サービスと通信するために使用する実際のアドレス) などの詳細情報を変更できます。  
  
 [バインディング](../../../docs/framework/wcf/bindings.md)  
 さらに、WCF には、クライアントとサービスの通信方法は、トランスポート、セキュリティ、およびエンコーディングが使用されるメッセージなどの最も基本的な機能をすばやく選択するためのバインディングの形式でのシステム指定のいくつかの一般的な構成が含まれています。  
  
 [エンドポイント](../../../docs/framework/wcf/endpoints.md)  
 を介して WCF サービスとすべての通信が行われます、*エンドポイント*サービス。 エンドポイントには、コントラクト、バインディングで指定されている構成情報、およびサービスの検索場所やサービスに関する情報の取得場所を示すアドレスが設定されています。  
  
 [サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)  
 WCF を使用して、既存のセキュリティ メカニズムでは、機密性、整合性、認証、および任意のサービスに承認を実装することができます。 また、セキュリティに関する成功および失敗を監査することも可能です。  
  
 [WS-I Basic Profile 1.1 の相互運用可能サービスの作成](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 他のプラットフォームやオペレーティング システム上で動作するサービスやクライアントと、相互に運用できるような形でサービスを配置するために必要な事項は、WS-I Basic Profile 1.1 の仕様に記載されています。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>関連項目  
 [基本的なプログラミング ライフサイクル](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [サービスの設計と実装](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)  
  
 [クライアントを構築する](../../../docs/framework/wcf/building-clients.md)  
  
 [拡張機能の概要](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [管理と診断](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a>関連項目

- [基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)
- [概念](../../../docs/framework/wcf/conceptual-overview.md)
- [WCF 機能の詳細](../../../docs/framework/wcf/feature-details/index.md)
