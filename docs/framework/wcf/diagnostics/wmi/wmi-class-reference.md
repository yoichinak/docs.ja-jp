---
title: WMI クラスの参照
ms.date: 03/30/2017
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
ms.openlocfilehash: 226e4dedecd152f3a3d4143280529c7823339932
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795874"
---
# <a name="wmi-class-reference"></a>WMI クラスの参照
ここでは、Windows Communication Foundation (WCF) WMI プロバイダーによって公開されるすべての WMI クラスの一覧を示します。  
  
## <a name="accessing-wmi-instances"></a>WMI インスタンスへのアクセス  
 WMI オブジェクト リファレンスに記載されているクラスはすべて、インスタンスを直接生成することはできません。ただし Service、AppDomain、Contract、ServiceAppDomain、ServiceToEndpointAssociation、Endpoint の各クラスを除きます。 他のインスタンスには、これらのトップ レベル クラスのプロパティからアクセスできます。 たとえば、TransportBindingElement インスタンスにアクセスするには、エンドポイントインスタンスから > バインド > BindingElements を使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ActivityTransfer](activitytransfer.md)  
  
 [AppDomainInfo](appdomaininfo.md)  
  
 [AspNetCompatibilityRequirementsAttribute](aspnetcompatibilityrequirementsattribute.md)  
  
 [AsymmetricSecurityBindingElement](asymmetricsecuritybindingelement.md)  
  
 "Behavior クラス"  
  
 [BinaryMessageEncodingBindingElement](binarymessageencodingbindingelement.md)  
  
 [バインド](binding.md)  
  
 [BindingElement](bindingelement.md)  
  
 [CallbackBehavior](callbackbehavior.md)  
  
 [チャネル クラス](channel-class.md)  
  
 [ChannelPoolSettings](channelpoolsettings.md)  
  
 [ClientCredentials](clientcredentials.md)  
  
 [ClientViaBehavior](clientviabehavior.md)  
  
 [CompositeDuplexBindingElement](compositeduplexbindingelement.md)  
  
 [ConnectionOrientedTransportBindingElement](connectionorientedtransportbindingelement.md)  
  
 [コントラクト](contract.md)  
  
 [CustomBindingElement](custombindingelement.md)  
  
 [DeliveryRequirementsAttribute](deliveryrequirementsattribute.md)  
  
 [エンドポイント](endpoint.md)  
  
 [HttpsTransportBindingElement](httpstransportbindingelement.md)  
  
 [HttpTransportBindingElement](httptransportbindingelement.md)  
  
 [LocalServiceSecuritySettings](localservicesecuritysettings.md)  
  
 [MatchAllEndpointBehavior](matchallendpointbehavior.md)  
  
 [MessageEncodingBindingElement](messageencodingbindingelement.md)  
  
 [MsmqBindingElementBase](msmqbindingelementbase.md)  
  
 [MsmqIntegrationBindingElement](msmqintegrationbindingelement.md)  
  
 [MsmqTransportBindingElement](msmqtransportbindingelement.md)  
  
 [MtomMessageEncodingBindingElement](mtommessageencodingbindingelement.md)  
  
 [MustUnderstandBehavior](mustunderstandbehavior.md)  
  
 [NamedPipeConnectionPoolSettings](namedpipeconnectionpoolsettings.md)  
  
 [NamedPipeTransportBindingElement](namedpipetransportbindingelement.md)  
  
 [OneWayBindingElement](onewaybindingelement.md)  
  
 "Operation クラス"  
  
 [OperationBehaviorAttribute](operationbehaviorattribute.md)  
  
 [PeerCustomResolverBindingElement](peercustomresolverbindingelement.md)  
  
 [PeerResolverBindingElement](peerresolverbindingelement.md)  
  
 [PeerSecuritySettings](peersecuritysettings.md)  
  
 [PeerTransportBindingElement](peertransportbindingelement.md)  
  
 [PeerTransportSecuritySettings](peertransportsecuritysettings.md)  
  
 [PnrpPeerResolverBindingElement](pnrppeerresolverbindingelement.md)  
  
 [PrivacyNoticeBindingElement](privacynoticebindingelement.md)  
  
 [ReliableSessionBindingElement](reliablesessionbindingelement.md)  
  
 [SecurityBindingElement](securitybindingelement.md)  
  
 [サービス](service.md)  
  
 [ServiceAppDomain](serviceappdomain.md)  
  
 [ServiceAuthorizationBehavior](serviceauthorizationbehavior.md)  
  
 [ServiceBehaviorAttribute](servicebehaviorattribute.md)  
  
 [ServiceCredentials](servicecredentials.md)  
  
 [ServiceDebugBehavior](servicedebugbehavior.md)  
  
 [ServiceMetadataBehavior](servicemetadatabehavior.md)  
  
 [ServiceSecurityAuditBehavior](servicesecurityauditbehavior.md)  
  
 [ServiceThrottlingBehavior](servicethrottlingbehavior.md)  
  
 [ServiceTimeoutsBehavior](servicetimeoutsbehavior.md)  
  
 [ServiceToEndpointAssociation](servicetoendpointassociation.md)  
  
 [SslStreamSecurityBindingElement](sslstreamsecuritybindingelement.md)  
  
 [SymmetricSecurityBindingElement](symmetricsecuritybindingelement.md)  
  
 [SynchronousReceiveBehavior](synchronousreceivebehavior.md)  
  
 [TcpConnectionPoolSettings](tcpconnectionpoolsettings.md)  
  
 [TcpTransportBindingElement](tcptransportbindingelement.md)  
  
 [TextMessageEncodingBindingElement](textmessageencodingbindingelement.md)  
  
 [TraceListener](tracelistener.md)  
  
 [TraceListenerArgument](tracelistenerargument.md)  
  
 [TransactedBatchingBehavior](transactedbatchingbehavior.md)  
  
 [TransactionFlowAttribute](transactionflowattribute.md)  
  
 [TransactionFlowBindingElement](transactionflowbindingelement.md)  
  
 [TransportBindingElement](transportbindingelement.md)  
  
 [TransportSecurityBindingElement](transportsecuritybindingelement.md)  
  
 [UseManagedPresentationBindingElement](usemanagedpresentationbindingelement.md)  
  
 [WindowsStreamSecurityBindingElement](windowsstreamsecuritybindingelement.md)  
  
 [WSAT_TraceEvent](wsat-traceevent.md)  
  
 [WSAT_TraceProvider](wsat-traceprovider.md)  
  
 [WSAT_TraceRecord](wsat-tracerecord.md)  
  
 [XmlDictionaryReaderQuotas](xmldictionaryreaderquotas.md)  
  
 [XmlSerializerOperationBehavior](xmlserializeroperationbehavior.md)
