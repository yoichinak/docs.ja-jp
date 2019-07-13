---
title: '方法: ProtectionLevel プロパティを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 77596d682af6f2579ca512b0a6de1694452e025b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928961"
---
# <a name="how-to-set-the-protectionlevel-property"></a>方法: ProtectionLevel プロパティを設定する
適切な属性を適用してプロパティを設定することで、保護レベルを設定できます。 サービス レベルですべてのメッセージのすべての部分に影響する保護を設定したり、メソッドからメッセージ部分まで、段階的にきめ細かなレベルで保護を設定したりすることができます。 詳細については、`ProtectionLevel`プロパティを参照してください[について保護レベル](../../../docs/framework/wcf/understanding-protection-level.md)します。  
  
> [!NOTE]
>  保護レベルは構成ではなく、コードでのみ設定できます。  
  
### <a name="to-sign-all-messages-for-a-service"></a>サービスのすべてのメッセージに署名するには  
  
1. サービス用のインターフェイスを作成します。  
  
2. 次のコードに示すように、<xref:System.ServiceModel.ServiceContractAttribute> 属性をサービスに適用し、<xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> プロパティを <xref:System.Net.Security.ProtectionLevel.Sign> に設定します (既定のレベルは <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>)。  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>操作のすべてのメッセージ部分に署名するには  
  
1. サービスのインターフェイスを作成し、このインターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> 属性を適用します。  
  
2. インターフェイスにメソッド宣言を追加します。  
  
3. 次のコードに示すように、メソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性を適用し、<xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> プロパティを <xref:System.Net.Security.ProtectionLevel.Sign> に設定します。  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>エラー メッセージの保護  
 サービスでスローされた例外は、SOAP エラーとしてクライアントに送信できます。 厳密に作成の詳細については、エラーを型指定されたを参照してください。[を指定すると処理のエラー コントラクトおよびサービスの](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)と[方法。サービス コントラクトでのエラーを宣言](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)します。  
  
#### <a name="to-protect-a-fault-message"></a>エラー メッセージを保護するには  
  
1. エラー メッセージを表す型を作成します。 次の例では、2 つのフィールドを持つ `MathFault` という名前のクラスを作成します。  
  
2. 次のコードに示すように、型に <xref:System.Runtime.Serialization.DataContractAttribute> 属性を適用し、シリアル化する必要のある各フィールドに <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用します。  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. エラーを返すインターフェイスで、エラーを返すメソッドに <xref:System.ServiceModel.FaultContractAttribute> 属性を適用し、エラー クラスの型に `detailType` パラメーターを設定します。  
  
4. 次のコードに示すように、コンストラクターでも、<xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> プロパティを <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> に設定します。  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>メッセージ部分の保護  
 メッセージ部分を保護するには、メッセージ コントラクトを使用します。 メッセージ コントラクトの詳細については、次を参照してください。 [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md)します。  
  
#### <a name="to-protect-a-message-body"></a>メッセージ本文を保護するには  
  
1. メッセージを表す型を作成します。 次の例では、`Company` と `CompanyName` の 2 つのフィールドを持つ `CompanyID` クラスを作成します。  
  
2. このクラスに <xref:System.ServiceModel.MessageContractAttribute> 属性を適用し、<xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> プロパティを <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> に設定します。  
  
3. メッセージ ヘッダーとして表現されるフィールドに <xref:System.ServiceModel.MessageHeaderAttribute> 属性を適用し、`ProtectionLevel` プロパティを <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> に設定します。  
  
4. 適用、 <xref:System.ServiceModel.MessageBodyMemberAttribute> 、メッセージ本文の一部として表現および設定される任意のフィールドに、`ProtectionLevel`プロパティを<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>次の例のようにします。  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>例  
 次の例では、サービスのいろいろな場所で、いくつかの属性クラスの `ProtectionLevel` プロパティを設定します。  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例のコンパイルに必要な名前空間を、次のコードに示します。  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [保護レベルの理解](../../../docs/framework/wcf/understanding-protection-level.md)
