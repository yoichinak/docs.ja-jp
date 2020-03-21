---
title: '方法 : セッションを必要とするサービスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184987"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>方法 : セッションを必要とするサービスを作成する
セッションでは、複数のエンドポイント間で共有される状態が作成されます。これにより、クライアントとサービス インスタンス間でのコールバック、マルチホップ セキュリティ、関連付けなどの便利な機能を使用できるようになります。 WCF (Wcf) アプリケーションのセッションの詳細については、「[セッションの使用](../../../../docs/framework/wcf/using-sessions.md)」を参照してください。  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>バインディングによるセッションのサポートを要求するコントラクトを指定するには  
  
1. 操作を 1 つ以上含むサービス コントラクトを作成します。 サービス コントラクトの作成方法の例については、「方法[: サービス コントラクトを定義する](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)」を参照してください。  
  
2. コントラクトを宣言する <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> を変更します。<xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> プロパティを次のいずれかに設定します。  
  
    - セッション内でこのコントラクトの実行を要求する場合は <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>。  
  
    - セッション内でこのコントラクトを実行できる場合は <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>。  
  
    - セッション内でこのコントラクトの実行を許可しない場合は <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>。  
  
3. セッションをサポートするバインディングを使用するようにサービス エンドポイントを構成します。 次の構成例は、WS<xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>ReliableMessaging セッションをサポートする `-` の使用方法を示しています。  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a>例  
 コントラクト レベルのセッション要件を指定し、構成ファイルを使用して、その要件を <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> バインディングでサポートする方法を、次のコード例に示します。  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
