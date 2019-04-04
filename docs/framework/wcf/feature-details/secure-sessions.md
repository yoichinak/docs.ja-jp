---
title: セキュリティで保護されたセッション
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 63e363e90a656c918b68d3f86d8b6ad3b7a540e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715713"
---
# <a name="secure-sessions"></a>セキュリティで保護されたセッション
Windows Communication Foundation (WCF) の機能とは、送信された順序でメッセージを受信することを保証する信頼できるセッションです。 このセクションの各トピックでは、信頼できるセッションを作成する際に考慮する必要のあるセキュリティへの影響について説明します。 信頼できるセッションの詳細については、[を使用してセッション](../../../../docs/framework/wcf/using-sessions.md)を参照してください。  
  
> [!NOTE]
>  Windows XP で偽装が必要な場合は、ステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用しない、セキュリティで保護されたセッションを使用します。 ステートフルな SCT が偽装と共に使用されると、<xref:System.InvalidOperationException> がスローされます。 詳細については、[サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|||  
|-|-|  
|[セキュリティ保護されたメッセージ交換とセッション](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|セキュリティで保護されたメッセージ交換とセキュリティで保護されたセッションは、同じ意味で使用されます。 ここでは、セキュリティで保護されたメッセージ交換のしくみ、およびこのパターンを使用する状況と理由について説明します。|  
|[方法: セキュリティで保護されたセッションを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|セキュリティで保護されたセッションの基本的な作成手順を説明するチュートリアルです。|  
|[方法: セキュリティ コンテキストを作成、セキュリティで保護されたセッションのトークン](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|クライアントの状態とセッションを保持する Web ファームを作成する手順について説明します。|  
|[セキュリティで保護されたセッションに関するセキュリティの検討](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|セキュリティで保護されたセッションに関する特別な考慮事項について説明します。|  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>関連項目  
 [セッション、インスタンス化、およびコンカレンシー](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [サービスの設計と実装](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>関連項目
- [方法: メッセージ リプレイ検出を有効にします。](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [方法: セッションを必要とするサービスを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
