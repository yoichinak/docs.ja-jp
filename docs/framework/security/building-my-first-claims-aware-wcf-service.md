---
title: クレーム対応の WCF サービスを初めて構築する
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: 13a17473388582e5fa72cd8d335b6a05204ea509
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792882"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>クレーム対応の WCF サービスを初めて構築する
## <a name="applies-to"></a>対象  
  
- Windows Identity Foundation (WIF)  
  
- Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>概要  
 このトピックでは、WIF を使用してクレーム対応 WCF サービスをビルドするシナリオの概要について説明します。 クレーム対応 Web サービスのシナリオには、通常、Web サービス、エンド ユーザー、セキュリティ トークン サービス (STS) の 3 つ参加要素が存在します。 次の図は、このシナリオについて説明しています。  
  
 ![WIF 基本クレーム対応 WCF サービスのコンポーネントを示す図。](./media/building-my-first-claims-aware-wcf-service/windows-identify-foundation-basic-claims-aware-windows-communication-foundation-service.gif)  
  
1. WCF サービス クライアント (エージェントと呼ばれることもあります) は、WIF を使用して資格情報を STS に送信します。認証が正常に行われると、STS はそのエージェントに対してトークンを発行します。  
  
2. エージェントは、この STS によって発行されたトークンを WCF サービスに送信します。  
  
3. クレーム対応 WCF サービスは、STS とその STS が発行したトークンを信頼するように構成され、 WIF を使用してトークンを検証し、解析します。 開発者は、承認の実装などのアプリケーションのニーズに応じて、適切な WIF API と種類 (**ClaimsPrincipal** など) を使用します。  
  
 .NET 4.5 以降、WIF は .NET Framework パッケージに含まれています。 .NET Framework で直接 WIF クラスを使用できるようになったため、.NET でクレームベースの ID をより深く統合できるようになり、クレームを簡単に使用できるようになりました。 WIF 4.5 を使用すると、クレーム対応アプリケーションの開発を開始する目的で、帯域外コンポーネントをインストールする必要がありません。 WIF クラスは、さまざまなアセンブリに分散されています。主なものは、System.Security.Claims、System.IdentityModel、および System.IdentityModel.Services です。  
  
 STS は、認証が正常に行われたときにトークンを発行するサービスです。 Microsoft では、2 つの業界標準 STS を提供します。  
  
- [Active Directory フェデレーション サービス (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Windows Azure の Access Control Service (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 AD FS 2.0 は、Windows Server R2 に含まれており、設置型シナリオの STS として使用できます。 Azure Active Directory アクセス制御 (Access Control Service または ACS とも呼ばれます) は、Microsoft Azure の一部として提供されるクラウド サービスです。 テストまたは学習の目的で、他の STS を使用して、クレーム対応アプリケーションをビルドすることもできます。 たとえばの一部であるローカルの開発用 STS を使用することができます、 [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849)は自由に利用できるオンライン。  
  
 WIF を使用して初めてクレーム対応 WCF サービスをビルドするを参照してください[How To:。WCF Web サービス アプリケーションの WIF を有効にする](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md)します。
  
## <a name="see-also"></a>関連項目

- [WIF の概要](../../../docs/framework/security/getting-started-with-wif.md)
