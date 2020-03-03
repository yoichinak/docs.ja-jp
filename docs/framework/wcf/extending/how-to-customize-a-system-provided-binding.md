---
title: '方法: システム指定のバインディングをカスタマイズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 6b92382b4a37168c33f9e97077ad292d27ea5bc3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797026"
---
# <a name="how-to-customize-a-system-provided-binding"></a>方法: システム指定のバインディングをカスタマイズする
Windows Communication Foundation (WCF) には、いくつかのシステム指定のバインディングが含まれています。これらを使用すると、基になるバインド要素の一部のプロパティを構成できますが、すべてのプロパティを構成することはできません。 ここでは、バインド要素のプロパティを設定してカスタム バインドを作成する方法を示します。  
  
 システム指定のバインディングを使用せずにバインド要素を直接作成および構成する方法の詳細については、「[カスタムバインド](custom-bindings.md)」を参照してください。  
  
 カスタムバインディングの作成と拡張の詳細については、「[バインディングの拡張](extending-bindings.md)」を参照してください。  
  
 WCF では、すべてのバインドは*バインド要素*で構成されます。 各バインド要素は <xref:System.ServiceModel.Channels.BindingElement> クラスから派生します。 <xref:System.ServiceModel.BasicHttpBinding> などのシステム指定のバインディングでは、独自のバインド要素が作成され構成されます。 ここでは、バインディングに直接公開されないこのバインド要素 (具体的には <xref:System.ServiceModel.BasicHttpBinding> クラス) のプロパティにアクセスして変更する方法を示します。  
  
 個々のバインド要素は、 <xref:System.ServiceModel.Channels.BindingElementCollection>クラスによって表されるコレクションに含まれ、次の順序で追加されます。トランザクションフロー、信頼できるセッション、セキュリティ、複合二重、一方向、ストリームセキュリティ、メッセージエンコーディング、トランスポート。 どのバインディングでも、これらすべてのバインド要素が必要になるとは限りません。 ユーザー定義のバインド要素も、このバインド要素のコレクションに表示されますが、前述の順序で表示される必要があります。 たとえば、ユーザー定義のトランスポートは、バインド要素コレクションの最後の要素となる必要があります。  
  
 <xref:System.ServiceModel.BasicHttpBinding> クラスには、次の 3 つのバインド要素が含まれています。  
  
1. オプションのセキュリティ バインド要素。HTTP トランスポートで使用される <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> クラス (メッセージ レベル セキュリティ)、またはトランスポート層がセキュリティを提供する場合 (HTTPS トランスポート) に使用される <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>。  
  
2. 必須のメッセージ エンコーダー バインド要素。<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> または <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>。  
  
3. 必須のトランスポート バインド要素。<xref:System.ServiceModel.Channels.HttpTransportBindingElement> または <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>。  
  
 この例では、バインドのインスタンスを作成し、そこから*カスタムバインド*を生成し、カスタムバインドのバインド要素を調べます。 HTTP バインド要素が見つかったら、その`KeepAliveEnabled`プロパティをに`false`設定します。 `KeepAliveEnabled` プロパティは、`BasicHttpBinding` に直接公開されていないので、カスタム バインドを作成し、バインド要素まで移動して、このプロパティを設定する必要があります。  
  
### <a name="to-modify-a-system-provided-binding"></a>システム標準のバインディングを変更するには  
  
1. <xref:System.ServiceModel.BasicHttpBinding> クラスのインスタンスを作成し、そのセキュリティ モードをメッセージ レベルに設定します。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. バインディングからカスタム バインディングを作成し、そのカスタム バインディングのプロパティの 1 つから <xref:System.ServiceModel.Channels.BindingElementCollection> クラスを作成します。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. <xref:System.ServiceModel.Channels.BindingElementCollection> クラスをループして <xref:System.ServiceModel.Channels.HttpTransportBindingElement> クラスが見つかったら、その <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> プロパティを `false` に設定します。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [カスタム バインディング](custom-bindings.md)
