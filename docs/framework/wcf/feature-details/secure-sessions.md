---
title: セキュリティで保護されたセッション
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 8f5cf9a965951bcc1049c2e96ae6cfa80b0113ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084970"
---
# <a name="secure-sessions"></a>セキュリティで保護されたセッション
Windows Communication Foundation (WCF) の機能とは、送信された順序でメッセージを受信することを保証する信頼できるセッションです。 このセクションの各トピックでは、信頼できるセッションを作成する際に考慮する必要のあるセキュリティへの影響について説明します。 信頼できるセッションの詳細については、次を参照してください。[を使用してセッション](../../../../docs/framework/wcf/using-sessions.md)します。  
  
> [!NOTE]
>  Windows XP で偽装が必要な場合は、ステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用しない、セキュリティで保護されたセッションを使用します。 ステートフルな SCT が偽装と共に使用されると、<xref:System.InvalidOperationException> がスローされます。 詳細については、次を参照してください。[サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)します。  
  
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
