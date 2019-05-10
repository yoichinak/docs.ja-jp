---
title: バインディングとセキュリティ
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 12296fbd503a7e9f1866f407964a5e223d1afadd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650332"
---
# <a name="bindings-and-security"></a>バインディングとセキュリティ
Windows Communication Foundation (WCF) に含まれるシステム指定のバインディングは、WCF アプリケーションをプログラムする簡単な方法を提供します。 1 つの例外を除き、すべてのバインディングにはセキュリティ スキームが含まれており、既定で有効になっています。 ここでは、セキュリティ ニーズに適した正しいバインディングの選択方法について説明します。  
  
 WCF セキュリティの概要については、次を参照してください。[セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)します。 WCF バインドを使用してプログラミングの詳細については、次を参照してください。 [WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)します。  
  
 バインディングを既に選択した場合のセキュリティに関連付けられている実行時の動作に関する詳細は見つかります[セキュリティ動作](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)します。  
  
 セキュリティ機能のなかには、システム指定のバインディングを使用してプログラミングできないものがあります。 詳細コントロールがカスタム バインドを使用して、次を参照してください。[カスタム バインドを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)します。  
  
## <a name="security-functions-of-bindings"></a>バインディングのセキュリティ機能  
 WCF には、ほとんどのニーズを満たすシステム指定のバインディング数が含まれています。 特定のバインディングでは不十分な場合は、カスタム バインドを作成することもできます。 システム指定のバインディングの一覧は、次を参照してください。 [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)します。 カスタム バインドの詳細については、次を参照してください。[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)します。  
  
 WCF でのすべてのバインドが 2 つの形式: API とは、構成ファイルで使用する XML 要素として。 たとえば、 `WSHttpBinding` (API) の対応が、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)します。  
  
 以下のセクションでは、各バインディングについて両方の形式を示し、セキュリティ機能の概要を説明します。  
  
### <a name="basichttp"></a>BasicHttp  
 コードでは、使用、<xref:System.ServiceModel.BasicHttpBinding>クラスは、構成を使用して、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)します。  
  
 このバインディングは、次のような既存のさまざまなテクノロジと共に使用できるようにデザインされています。  
  
- ASP.NET Web サービス (ASMX) Version 1  
  
- Web サービス拡張 (WSE) アプリケーション  
  
- Web サービス相互運用性で定義されている基本プロファイル (WS-は) 仕様 (<https://go.microsoft.com/fwlink/?LinkId=38955>)。  
  
- WS-I で定義されている基本セキュリティ プロファイル  
  
 既定では、このバインディングはセキュリティで保護されません。 ASMX サービスと相互運用するように設計されています。 セキュリティを有効にした場合、このバインディングは、インターネット インフォメーション サービス (IIS: Internet Information Services) のセキュリティ機構 (基本認証、ダイジェスト、Windows 統合セキュリティなど) とシームレスに相互運用できるように設計されています。 詳細については、次を参照してください。[トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)します。 このバインディングでは、以下をサポートしています。  
  
- HTTPS トランスポート セキュリティ  
  
- HTTP 基本認証  
  
- WS-Security。  
  
 詳細については、「<xref:System.ServiceModel.BasicHttpSecurity>」、「<xref:System.ServiceModel.BasicHttpMessageSecurity>」、「<xref:System.ServiceModel.BasicHttpMessageCredentialType>」、および「<xref:System.ServiceModel.BasicHttpSecurityMode>」を参照してください。  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 コードでは、使用、<xref:System.ServiceModel.WSHttpBinding>クラスは、構成を使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)します。  
  
 既定では、このバインディングは WS-Security 仕様を実装しており、WS-* 仕様を実装するサービスとの相互運用性があります。 次のセキュリティをサポートします。  
  
- HTTPS トランスポート セキュリティ  
  
- WS-Security。  
  
- SOAP メッセージ資格情報セキュリティを使用した、HTTPS トランスポート保護による呼び出し元の認証。  
  
 詳細については、次を参照してください。 <xref:System.ServiceModel.WSHttpSecurity>、 <xref:System.ServiceModel.MessageSecurityOverHttp>、 <xref:System.ServiceModel.MessageCredentialType>、 <xref:System.ServiceModel.SecurityMode>、 <xref:System.ServiceModel.HttpTransportSecurity>、 <xref:System.ServiceModel.HttpClientCredentialType>、および<xref:System.ServiceModel.HttpProxyCredentialType>します。  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 コードでは、使用、<xref:System.ServiceModel.WSDualHttpBinding>クラスは、構成を使用して、 [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)します。  
  
 このバインディングは、双方向サービス アプリケーションを有効にするために設計されています。 このバインディングは、メッセージ ベースの転送セキュリティ用に WS-Security 仕様を実装しています。 トランスポート セキュリティは使用できません。 既定では、次の機能を提供します。  
  
- WS-ReliableMessaging を実装して信頼性を確保します。  
  
- WS-Security を実装して転送セキュリティおよび認証を実現します。  
  
- HTTP を使用してメッセージを配信します。  
  
- テキスト/XML メッセージ エンコーディングを使用します。  
  
 バインディングで WS-Security (メッセージ層セキュリティ) を使用すると、次のパラメーターを構成できるようになります。  
  
- 暗号アルゴリズムを決定するためのセキュリティ アルゴリズム スイート  
  
- 以下を行うためのバインディング オプション  
  
    - クライアントで帯域外で使用可能なサービス資格情報の提供  
  
    - チャネル セットアップの一部としてサービスからネゴシエートされるサービス資格情報の提供  
  
 詳細については、次のトピックを参照してください。 <xref:System.ServiceModel.WSDualHttpSecurity> および <xref:System.ServiceModel.WSDualHttpSecurityMode>  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 コードでは、使用、<xref:System.ServiceModel.NetTcpBinding>クラスは、構成を使用して、 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)します。  
  
 このバインディングは複数のコンピューター間での通信に最適化されています。 既定では、次の特性があります。  
  
- トランスポート層セキュリティを実装します。  
  
- Windows セキュリティを利用して、転送セキュリティと認証を確保します。  
  
- トランスポートに TCP を使用します。  
  
- バイナリ メッセージのエンコードを実装します。  
  
- WS-ReliableMessaging を実装します。  
  
 選択できる方法は次のとおりです。  
  
- メッセージ層セキュリティ (WS-Security を使用)  
  
- メッセージ資格情報を使用するトランスポート セキュリティ (TLS (Transport Layer Security) over TCP によって実現される機密性と整合性、および WS-Security によって提供される承認に使用する資格情報)  
  
 詳細については、次を参照してください。 <xref:System.ServiceModel.NetTcpSecurity>、 <xref:System.ServiceModel.TcpTransportSecurity>、 <xref:System.ServiceModel.TcpClientCredentialType>、 <xref:System.ServiceModel.MessageSecurityOverTcp>、および<xref:System.ServiceModel.MessageCredentialType>します。  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 コードでは、使用、<xref:System.ServiceModel.NetNamedPipeBinding>クラスは、構成を使用して、 [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)します。  
  
 このバインディングは、(通常では同じコンピューター上の) 複数プロセス間の通信に最適化されています。 既定では、このバインディングには次の特性があります。  
  
- トランスポート セキュリティを使用して、メッセージ転送と認証を実現します。  
  
- 名前付きパイプを使用してメッセージを配信します。  
  
- バイナリ メッセージのエンコードを実装します。  
  
- 暗号化とメッセージの署名を使用します。  
  
 選択できる方法は次のとおりです。  
  
- Windows セキュリティを使用した認証  
  
 詳細については、「<xref:System.ServiceModel.NetNamedPipeSecurity>「<xref:System.ServiceModel.NetNamedPipeSecurityMode>および「<xref:System.ServiceModel.NamedPipeTransportSecurity>」を参照してください。  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 コードでは、使用、<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>クラスは、構成を使用して、 [ \<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)します。  
  
 このバインディングは、非-WCF Microsoft Message Queuing MSMQ エンドポイントで WCF クライアントと相互運用可能なサービスを作成するために最適化されます。  
  
 既定では、このバインディングはトランスポート セキュリティを使用し、次のセキュリティ特性があります。  
  
- セキュリティは無効 (なし) にできます。  
  
- MSMQ トランスポート セキュリティ (トランスポート)。  
  
 詳細については、次のトピックを参照してください。 <xref:System.ServiceModel.NetMsmqSecurity> および <xref:System.ServiceModel.NetMsmqSecurityMode>  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 コードでは、使用、<xref:System.ServiceModel.NetMsmqBinding>クラスは、構成を使用して、 [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)します。  
  
 このバインディングは、キューに置かれたメッセージのサポートの MSMQ を必要とする WCF サービスを作成するときに使用するものは。  
  
 既定では、このバインディングはトランスポート セキュリティを使用し、次のセキュリティ特性があります。  
  
- セキュリティは無効 (なし) にできます。  
  
- MSMQ トランスポート セキュリティ (トランスポート)。  
  
- SOAP に基づくメッセージ セキュリティ (メッセージ)。  
  
- トランスポート セキュリティとメッセージ セキュリティ (両方)。  
  
- クライアント資格情報の種類がサポートされています。None、Windows、UserName、証明書、IssuedToken。  
  
 <xref:System.ServiceModel.MessageCredentialType.Certificate> 資格情報は、セキュリティ モードが <xref:System.ServiceModel.NetMsmqSecurityMode.Both> または <xref:System.ServiceModel.NetMsmqSecurityMode.Message> に設定されている場合にのみサポートされます。  
  
 詳細については、次のトピックを参照してください。 <xref:System.ServiceModel.MessageSecurityOverMsmq> および <xref:System.ServiceModel.MsmqTransportSecurity>  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 コードでは、使用、<xref:System.ServiceModel.WSFederationHttpBinding>クラスは、構成を使用して、 [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)します。  
  
 既定では、このバインディングは WS-Security (メッセージ層セキュリティ) を使用します。  
  
 詳細については、次を参照してください。[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)、 <xref:System.ServiceModel.WSFederationHttpSecurity>、および<xref:System.ServiceModel.WSFederationHttpSecurityMode>します。  
  
## <a name="custom-bindings"></a>カスタム バインディング  
 システム指定のバインディングがいずれも要件を満たさない場合は、カスタム セキュリティ バインド要素を使用してカスタム バインドを作成できます。 詳細については、次を参照してください。[カスタム バインドを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)します。  
  
## <a name="binding-choices"></a>バインディングの選択肢  
 次の表は、セキュリティ モード設定で提供される機能をまとめたものです。つまり、セキュリティ モードを `Transport`、`Message`、または `TransportWithMessageCredential` に設定したときに使用できる機能の一覧です。 アプリケーションで必要なセキュリティ機能を決定するときに、この表を参考にしてください。  
  
|設定|機能|  
|-------------|--------------|  
|Transport|サーバー認証<br /><br /> クライアント認証<br /><br /> Point-to-Point のセキュリティ<br /><br /> 相互運用性<br /><br /> ハードウェアの高速化<br /><br /> 高いスループット<br /><br /> セキュリティで保護されたファイアウォール<br /><br /> 待ち時間の長いアプリケーション<br /><br /> 複数のホップでの再暗号化|  
|メッセージ|サーバー認証<br /><br /> クライアント認証<br /><br /> エンド ツー エンドのセキュリティ<br /><br /> 相互運用性<br /><br /> 多様なクレーム<br /><br /> フェデレーション<br /><br /> 複数要因の認証<br /><br /> カスタム トークン<br /><br /> Notary/Timestamp サービス<br /><br /> 待ち時間の長いアプリケーション<br /><br /> メッセージ署名の永続化|  
|TransportWithMessageCredential|サーバー認証<br /><br /> クライアント認証<br /><br /> Point-to-Point のセキュリティ<br /><br /> 相互運用性<br /><br /> ハードウェアの高速化<br /><br /> 高いスループット<br /><br /> 多様なクライアント クレーム<br /><br /> フェデレーション<br /><br /> 複数要因の認証<br /><br /> カスタム トークン<br /><br /> セキュリティで保護されたファイアウォール<br /><br /> 待ち時間の長いアプリケーション<br /><br /> 複数のホップでの再暗号化|  
  
 さまざまなモード設定をサポートするバインディングを次の表に示します。 サービス エンドポイントを作成するときは、使用するバインディングをこの表から選択してください。  
  
|バインド|トランスポート モードのサポート|メッセージ モードのサポート|TransportWithMessageCredential のサポート|  
|-------------|----------------------------|--------------------------|--------------------------------------------|  
|`BasicHttpBinding`|[はい]|はい|はい|  
|`WSHttpBinding`|はい|はい|[はい]|  
|`WSDualHttpBinding`|×|はい|×|  
|`NetTcpBinding`|[はい]|はい|はい|  
|`NetNamedPipeBinding`|[はい]|×|×|  
|`NetMsmqBinding`|[はい]|[はい]|×|  
|`MsmqIntegrationBinding`|はい|×|×|  
|`wsFederationHttpBinding`|×|[はい]|[はい]|  
  
## <a name="transport-credentials-in-bindings"></a>バインディングにおけるトランスポート資格情報  
 トランスポート セキュリティ モードで `BasicHttpBinding` または `WSHttpBinding` を使用するときに使用できるクライアント資格情報の種類を、次の表に示します。  
  
|型|説明|  
|----------|-----------------|  
|なし|クライアントが資格情報を提示する必要がないことを指定します。 匿名クライアントであると解釈されます。|  
|Basic|基本認証です。 詳細については、HTTP 認証の RFC 2617 を参照してください。基本認証とダイジェスト認証で使用可能な<https://go.microsoft.com/fwlink/?LinkId=84023>します。|  
|Digest|ダイジェスト認証です。 詳細については、HTTP 認証の RFC 2617 を参照してください。基本認証とダイジェスト認証で使用可能な<https://go.microsoft.com/fwlink/?LinkId=84023>します。|  
|NTLM|NTLM (NT LAN Manager) 認証です。|  
|Windows|Windows 認証です。|  
|証明書|証明書を使用して実行される認証です。|  
|IssuedToken|セキュリティ トークン サービスまたは [!INCLUDE[infocard](../../../../includes/infocard-md.md)] によって発行されたトークンを使用したクライアントの認証を、サービスが要求できるようにします。 詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)します。|  
  
### <a name="message-client-credentials-in-bindings"></a>バインディングにおけるメッセージ クライアント資格情報  
 メッセージ セキュリティ モードでバインディングを使用するときに使用できるクライアント資格情報の種類を次の表に示します。  
  
|型|説明|  
|----------|-----------------|  
|なし|サービスが匿名クライアントとやり取りを行うことが可能になります。|  
|Windows|Windows 資格情報の認証済みコンテキストの制御下で SOAP メッセージ交換を行うことができます。|  
|UserName|サービスが、ユーザー名資格情報を使用したクライアントの認証を要求できるようにします。 セキュリティ モードに設定されている場合は注意`TransportWithMessageCredential`WCF は、パスワード ダイジェストや派生キー パスワードを使用して、このようなキー メッセージ モード セキュリティを使用したりの送信をサポートしていません。 そのため、WCF は、ユーザー名資格情報を使用する場合、トランスポート、セキュリティで保護を適用します。|  
|証明書|証明書を使用したクライアントの認証を、サービスで要求することが可能になります。|  
|IssuedToken|サービスは、セキュリティ トークン サービスを使用してカスタム トークンを提供できます。|  
  
## <a name="see-also"></a>関連項目

- [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [資格情報の種類の選択](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [カスタム バインドを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [セキュリティ動作](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Windows Server App Fabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
