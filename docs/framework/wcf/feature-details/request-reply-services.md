---
title: 要求/応答サービス
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 1ff11b1cae4ec8f6fe886a55cb0add27831048d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177815"
---
# <a name="request-reply-services"></a>要求/応答サービス
要求/応答サービスは、操作コントラクトでは、Windows Communication Foundation (WCF) の既定の種類です。 クライアントはサービス操作を呼び出し、サービスからの応答を待機します。 サービス操作の呼び出しは、同期的または非同期的に実行できます。同期呼び出しでは、応答を受信するか、呼び出しがタイムアウトするまで、クライアントがブロックされます。非同期呼び出しでは、クライアントはサービス操作の呼び出し後、動作を続行し、別のスレッドのサービスからの応答を受信できます。  
  
 要求/応答サービス コントラクトを作成するには、サービス コントラクトを定義し、次のサンプル コードに示すように <xref:System.ServiceModel.OperationContractAttribute> クラスを各操作に適用します。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 これは既定の動作であるため、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティを `false` に設定する必要はありません。  
  
## <a name="see-also"></a>関連項目

- [一方向サービス](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [双方向サービス](../../../../docs/framework/wcf/feature-details/duplex-services.md)
