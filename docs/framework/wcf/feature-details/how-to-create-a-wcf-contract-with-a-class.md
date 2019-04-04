---
title: '方法: クラスを持つ、Windows Communication Foundation コントラクトを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: b32d4feb03daac33af8b7ca3b533a0b7013bb090
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658927"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>方法: クラスを持つ、Windows Communication Foundation コントラクトを作成します。
インターフェイスを使用する Windows Communication Foundation (WCF) コントラクトを作成することをお勧めです。 詳細については、「[方法 :サービス コントラクトを定義する](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)します。 ここで説明する代替方法では、クラスを作成してから、<xref:System.ServiceModel.ServiceContractAttribute> 属性を直接そのクラスに適用し、<xref:System.ServiceModel.OperationContractAttribute> 属性をコントラクトに含まれるクラス内の各メソッドに適用します。  
  
> [!WARNING]
>  `[ServiceContract]` と `[ServiceContractAttribute]` は、同じことを行います。 同じことが当てはまります`[OperationContract]`と`[OperationContractAttribute]`します。 各ケースでは、後者の短縮形です。  
  
 サービス コントラクトの詳細については、[Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md)を参照してください。  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>クラスを使用した Windows Communication Foundation コントラクトの作成  
  
1.  Visual Basic を使用して新しいクラスを作成C#、またはその他の共通言語ランタイム言語。  
  
2.  クラスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。  
  
3.  クラスでメソッドを作成します。  
  
4.  適用、<xref:System.ServiceModel.OperationContractAttribute>パブリックの WCF コントラクトの一部として公開する必要がある各メソッドにクラス。  
  
## <a name="example"></a>例  
 次のコード例は、サービス コントラクトを定義するクラスを示しています。  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求/応答メッセージ パターンを使用します。 このメッセージ パターンの詳細については、次を参照してください。[方法。要求/応答コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)します。 属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。 その他の例については、「[方法:一方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)と[方法。双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
