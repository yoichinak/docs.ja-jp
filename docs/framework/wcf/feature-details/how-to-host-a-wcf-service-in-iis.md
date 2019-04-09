---
title: '方法: IIS で WCF サービスをホストする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 8b2ebc108bf3eef60e8877e617acec782da38fa4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124554"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>方法: IIS で WCF サービスをホストする
このトピックでは、インターネット インフォメーション サービス (IIS) でホストされている Windows Communication Foundation (WCF) サービスを作成するために必要な基本的な手順について説明します。 このトピックは、IIS に関する知識があり、IIS 管理ツールを使用して IIS アプリケーションを作成および管理する方法を理解していることを前提としています。 IIS の詳細については、次を参照してください。[インターネット インフォメーション サービス](https://go.microsoft.com/fwlink/?LinkId=132449)します。 IIS 環境での実行がプロセスのリサイクルなどの IIS 機能を最大限に活用する WCF サービスはアイドル シャット ダウン、処理状況の監視、およびメッセージ ベースのアクティブ化します。 このホスト オプションでは、IIS が正しく構成されている必要がありますが、アプリケーションの一部としてホスト コードを書く必要はありません。 IIS ホストは、HTTP トランスポートでのみ使用できます。  
  
 方法の詳細についての WCF と[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]操作は、「 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)します。 セキュリティの構成の詳細については、次を参照してください。[セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)します。  
  
 この例のソースのコピーを次を参照してください。 [IIS は、インラインのコードを使用してホスト](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)します。  
  
### <a name="to-create-a-service-hosted-by-iis"></a>IIS でホストされるサービスを作成するには  
  
1.  コンピューターに IIS がインストールされ、実行されていることを確認します。 インストールと IIS の構成の詳細については、次を参照してください[のインストールと IIS 7.0 の構成。](https://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  アプリケーション ファイル用に "IISHostedCalcService" という新しいフォルダーを作成し、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] がそのフォルダーの内容にアクセスできることを確認します。次に、IIS 管理ツールを使用して、このアプリケーション ディレクトリに物理的に配置する新しい IIS アプリケーションを作成します。 アプリケーション ディレクトリのエイリアスを作成する場合は、"IISHostedCalc" を使用します。  
  
3.  "service.svc" という新しいファイルをアプリケーション ディレクトリに作成します。 次を追加してこのファイルを編集@ServiceHost要素。  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  アプリケーション ディレクトリ内に App_Code サブディレクトリを作成します。  
  
5.  App_Code サブディレクトリに Service.cs というコード ファイルを作成します。  
  
6.  Service.cs ファイルの先頭に次の using ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  using ステートメントの後に、次の名前空間宣言を追加します。  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  次のコードに示すように、名前空間宣言内にサービス コントラクトを定義します。  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. 次のコードに示すように、サービス コントラクト定義の後に、サービス コントラクトを実装します。  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. アプリケーション ディレクトリ内に "Web.config" というファイルを作成し、次の構成コードをファイルに追加します。 WCF インフラストラクチャは、実行時に情報を使用して、クライアント アプリケーションが通信できるエンドポイントを作成します。  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     この例では、構成ファイルにエンドポイントを明示的に指定します。 エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。 既定のエンドポイント、バインディング、および動作を参照の詳細については[Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)と[Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)します。  
  
11. サービスが正常にホストされていることを確認するには、サービスの URL を参照し、Internet Explorer のインスタンスを開きます。 `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>例  
 IIS がホストする電卓サービスのコードの完全な一覧を次に示します。  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>関連項目

- [インターネット インフォメーション サービスでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)
- [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)
- [AppFabric のホスティング機能](https://go.microsoft.com/fwlink/?LinkId=201276)
