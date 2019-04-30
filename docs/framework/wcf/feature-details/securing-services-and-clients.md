---
title: サービスおよびクライアントのセキュリティ保護
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: e455c7a48e1484d5acdcc5f6cdc9098997a3ba83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990939"
---
# <a name="securing-services-and-clients"></a>サービスおよびクライアントのセキュリティ保護
このセクションの情報は、Windows Communication Foundation (WCF) のセキュリティのプログラミングについて説明します。 一般に、これには、システムが提供する適切なバインディングを選択すること、セキュリティ要素のプロパティを適切に設定すること、サービス側/クライアント側で使う資格情報の検索方法にまつわる、サービスの動作に関するプロパティを適切に設定することなどが含まれます。 ように、これらの手法はほとんどのシナリオでは、ほとんどのユーザーのセキュリティ要件をカバー[一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)します。 実際のシナリオでは、多くの機能が必要とする場合が初めて表示[カスタム バインドを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); ソリューションは、明らかなかどうかは、次を参照してください。[拡張セキュリティ](../../../../docs/framework/wcf/extending/extending-security.md)。 作成 (またはとの相互運用) に多様なクレームを使用するシステムでは、トピックを参照して[承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 メッセージを保護するために使うプログラミング モデルの概要  
  
 [トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 トランスポート層を介してやり取りするメッセージを保護する方法の概要  
  
 [メッセージのセキュリティ](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 Windows Communication Foundation (WCF) メッセージ レベルのセキュリティを使用する理由をまとめたものです。  
  
 [セキュリティで保護されたセッション](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 WCF のセッションをセキュリティで保護するときに必要な考慮事項について説明します。  
  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 X.509 証明書を使用する際に必要となる主なタスクの解説  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>関連項目  
 [セキュリティの概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [カスタム バインドを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>関連項目

- [基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Windows Server App Fabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
