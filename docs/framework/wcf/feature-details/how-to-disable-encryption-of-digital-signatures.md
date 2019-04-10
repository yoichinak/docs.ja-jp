---
title: '方法: デジタル署名の暗号化を無効にする'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 6f5004224f66f2961efc3ee920989487273c3eff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192122"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>方法: デジタル署名の暗号化を無効にする
既定では、メッセージは署名され、署名はデジタル暗号化されます。 これは、<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> のインスタンスを使用してカスタム バインドを作成し、いずれかのクラスの `MessageProtectionOrder` プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder> 列挙値に設定することによって制御されます。 既定値は <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> です。 このプロセスは、単に署名して暗号化する場合よりも、メッセージ全体のサイズによって最大で 30 パーセントほど長い時間がかかります (メッセージが小さいほどパフォーマンスへの影響は大きくなります)。 ただし、署名の暗号化を無効にすると、攻撃者がメッセージの内容を予想できるようになる危険性があります。 その理由は、メッセージ内のすべての署名部分のプレーン テキストのハッシュ コードが署名要素に含まれるからです。 たとえば、メッセージ本体は既定で暗号化されますが、暗号化されていない署名には、暗号化される前のメッセージ本体のハッシュ コードが含まれます。 署名および暗号化された部分に指定できる一連の値が小さい場合、攻撃者にハッシュ値を参照され、内容を推測されてしまうおそれがあります。 署名を暗号化すると、このような攻撃は軽減します。  
  
 そのため、署名の暗号化を無効にするのは、コンテンツの重要性が低いか、または指定できる一連のコンテンツの値が大きくて非決定性があり、前述の攻撃を軽減するよりもパフォーマンスの向上が重要な場合に限定してください。  
  
> [!NOTE]
>  メッセージ内に暗号化する対象が存在しない場合は、<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティまたは <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティが <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> に設定されていても、署名要素は暗号化されません。 この動作は、システム指定のバインディングでも発生します。すべてのシステム指定のバインディングには、メッセージを保護する順序が `SignBeforeEncryptAndEncryptSignature` に設定されています。 ただし、Web サービス記述言語 (WSDL) WCF にはなりますが生成されますが残っているので、`<sp:EncryptSignature>`アサーション。  
  
### <a name="to-disable-digital-signing"></a>デジタル署名を無効にするには  
  
1.  <xref:System.ServiceModel.Channels.CustomBinding> を作成します。 詳細については、「[方法 :SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)します。  
  
2.  <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> をバインディング コレクションに追加します。  
  
3.  <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> に設定するか、または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> に設定します。  
  
## <a name="see-also"></a>関連項目

- [カスタム バインドを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
