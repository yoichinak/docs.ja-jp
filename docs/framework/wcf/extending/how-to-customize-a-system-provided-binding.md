---
title: '方法: システム指定のバインディングをカスタマイズします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 7447830de81471c6d9e5b7812ec7a0ad1dbd2ccf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704707"
---
# <a name="how-to-customize-a-system-provided-binding"></a>方法: システム指定のバインディングをカスタマイズします。
Windows Communication Foundation (WCF) には、基になるバインド要素のプロパティの一部がすべてのプロパティを構成するためのいくつかのシステム指定のバインディングが含まれています。 ここでは、バインド要素のプロパティを設定してカスタム バインドを作成する方法を示します。  
  
 直接作成し、システム指定のバインディングを使用せず、バインド要素を構成する方法の詳細については、[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)を参照してください。  
  
 作成して、カスタム バインディングの拡張の詳細については、[バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)を参照してください。  
  
 WCF ですべてのバインドで構成されて*バインド要素*します。 各バインド要素は <xref:System.ServiceModel.Channels.BindingElement> クラスから派生します。 <xref:System.ServiceModel.BasicHttpBinding> などのシステム指定のバインディングでは、独自のバインド要素が作成され構成されます。 ここでは、バインディングに直接公開されないこのバインド要素 (具体的には <xref:System.ServiceModel.BasicHttpBinding> クラス) のプロパティにアクセスして変更する方法を示します。  
  
 によって表されるコレクションに含まれる個別のバインド要素、<xref:System.ServiceModel.Channels.BindingElementCollection>クラスし、この順序で追加されます。トランザクション フロー、信頼できるセッション、セキュリティ、複合二重、一方向、Stream のセキュリティ、メッセージ エンコーディング、およびトランスポート。 どのバインディングでも、これらすべてのバインド要素が必要になるとは限りません。 ユーザー定義のバインド要素も、このバインド要素のコレクションに表示されますが、前述の順序で表示される必要があります。 たとえば、ユーザー定義のトランスポートは、バインド要素コレクションの最後の要素となる必要があります。  
  
 <xref:System.ServiceModel.BasicHttpBinding> クラスには、次の 3 つのバインド要素が含まれています。  
  
1.  オプションのセキュリティ バインド要素。HTTP トランスポートで使用される <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> クラス (メッセージ レベル セキュリティ)、またはトランスポート層がセキュリティを提供する場合 (HTTPS トランスポート) に使用される <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>。  
  
2.  必須のメッセージ エンコーダー バインド要素。<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> または <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>。  
  
3.  必須のトランスポート バインド要素。<xref:System.ServiceModel.Channels.HttpTransportBindingElement> または <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>。  
  
 この例で バインドのインスタンスを作成、生成、*カスタム バインド*、そこから、カスタム バインディングでバインド要素を確認し、HTTP バインド要素を見つけることとその`KeepAliveEnabled`プロパティを`false`. `KeepAliveEnabled` プロパティは、`BasicHttpBinding` に直接公開されていないので、カスタム バインドを作成し、バインド要素まで移動して、このプロパティを設定する必要があります。  
  
### <a name="to-modify-a-system-provided-binding"></a>システム標準のバインディングを変更するには  
  
1.  <xref:System.ServiceModel.BasicHttpBinding> クラスのインスタンスを作成し、そのセキュリティ モードをメッセージ レベルに設定します。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  バインディングからカスタム バインディングを作成し、そのカスタム バインディングのプロパティの 1 つから <xref:System.ServiceModel.Channels.BindingElementCollection> クラスを作成します。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  <xref:System.ServiceModel.Channels.BindingElementCollection> クラスをループして <xref:System.ServiceModel.Channels.HttpTransportBindingElement> クラスが見つかったら、その <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> プロパティを `false` に設定します。  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)
