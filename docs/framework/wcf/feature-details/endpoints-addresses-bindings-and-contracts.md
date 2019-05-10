---
title: エンドポイント:アドレス、バインディング、およびコントラクト
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3d345cfa3169e22e7c5e85cd1c7d11c2feef4f5f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665959"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>エンドポイント:アドレス、バインディング、およびコントラクト
を介して Windows Communication Foundation (WCF) サービスとすべての通信が行われます、*エンドポイント*サービス。 エンドポイントは、WCF サービスによって提供される機能へのアクセスをクライアントに提供します。  
  
 各エンドポイントは、次の 4 つのプロパティで構成されます。  
  
- そのエンドポイントの場所を示すアドレス。  
  
- クライアントがエンドポイントと通信する方法を指定するバインディング。  
  
- 利用可能な操作を識別するためのコントラクト。  
  
- エンドポイントのローカル実装の詳細を指定する一連の動作。  
  
 このトピックでは、エンドポイントの構造について説明し、WCF オブジェクト モデルでの表現方法について説明します。  
  
## <a name="the-structure-of-an-endpoint"></a>エンドポイントの構造  
 各エンドポイントの構造は次のとおりです。  
  
- アドレス:アドレスは一意にエンドポイントを識別し、潜在的な指示があるサービスのコンシューマーです。 WCF オブジェクト モデルで表されます、<xref:System.ServiceModel.EndpointAddress>クラス。 <xref:System.ServiceModel.EndpointAddress> クラスには次のものが含まれます。  
  
    - <xref:System.ServiceModel.EndpointAddress.Uri%2A> プロパティは、サービスのアドレスを表します。  
  
    - <xref:System.ServiceModel.EndpointAddress.Identity%2A> プロパティは、サービスのセキュリティ ID とオプションのメッセージ ヘッダーのコレクションを表します。 オプションのメッセージ ヘッダーは、エンドポイントの識別またはエンドポイントとの対話のための、より詳細なアドレス指定情報を追加するために使用されます。  
  
     詳細については、次を参照してください。[エンドポイント アドレスを指定する](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)します。  
  
- バインディング:バインディングはエンドポイントとの通信方法を指定します。 バインディングには、以下の項目が含まれます。  
  
    - 使用するトランスポート プロトコル (例 : TCP や HTTP)。  
  
    - メッセージに使用するエンコーディング (例 : テキストやバイナリ)。  
  
    - 必要なセキュリティ要件 (例 : SSL メッセージ セキュリティや SOAP メッセージ セキュリティ)。  
  
     詳細については、次を参照してください。 [WCF のバインディングの概要](../../../../docs/framework/wcf/bindings-overview.md)します。 バインディングは抽象基本クラスで WCF オブジェクト モデルで表される<xref:System.ServiceModel.Channels.Binding>します。 ほとんどのシナリオでは、システム指定のバインディングを使用できます。 詳細については、次を参照してください。 [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)します。  
  
- コントラクト:コントラクトでは、クライアントに公開するエンドポイント機能について説明します。 コントラクトは、以下の項目を指定します。  
  
    - クライアントから呼び出すことができる操作。  
  
    - メッセージの形式。  
  
    - 操作を呼び出すために必要な入力パラメーターまたはデータの型。  
  
    - クライアントが予期できる処理メッセージまたは応答メッセージの種類。  
  
     コントラクトを定義する詳細については、次を参照してください。 [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md)します。  
  
- 動作:エンドポイントの動作を使用して、サービス エンドポイントのローカル動作をカスタマイズすることができます。 エンドポイントの動作は、WCFruntime の作成プロセスで参加することでこれを実現します。 エンドポイントの動作の一例は、<xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> プロパティです。このプロパティにより、SOAP アドレスまたは Web サービス記述言語 (WSDL) アドレスとは異なるリッスン アドレスを指定できます。 詳細については、次を参照してください。 [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)します。  
  
## <a name="defining-endpoints"></a>エンドポイントの定義  
 サービスのエンドポイントは、コードを使用して強制的に指定するか、構成を介して宣言として指定することができます。 詳細については、「[方法 :サービス エンドポイントの構成で作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)と[方法。コードでサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 このセクションでは、バインディング、エンドポイント、およびアドレスの目的を説明し、バインディングとエンドポイントの構成方法および `ClientVia` 動作と `ListenUri` プロパティの使用方法を示します。  
  
 [アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 Wcf エンドポイントのアドレス指定する方法について説明します。  
  
 [バインディング](../../../../docs/framework/wcf/feature-details/bindings.md)  
 バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定する方法について説明します。  
  
 [コントラクト](../../../../docs/framework/wcf/feature-details/contracts.md)  
 コントラクトでサービスのメソッドが定義されるしくみについて説明します。  
  
 [方法: 構成でサービス エンドポイントを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 構成にサービス エンドポイントを作成する方法について説明します。  
  
 [方法: コードでサービス エンドポイントを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 コード内にサービス エンドポイントを作成する方法について説明します。  
  
 [方法: Svcutil.exe を使用して、コンパイル済みサービス コードを検証するには](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 使用してサービスをホストせず、サービス実装と構成でエラーを検出する方法について説明します、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。  
  
## <a name="see-also"></a>関連項目

- [サービスの構成](../../../../docs/framework/wcf/configuring-services.md)
- [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)
