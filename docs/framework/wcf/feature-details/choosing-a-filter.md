---
title: フィルターの選択
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: f634363a3f8b69b38fd4d313c42de4d742d94acc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514194"
---
# <a name="choosing-a-filter"></a>フィルターの選択
ルーティング サービスを構成する際には、適切なメッセージ フィルターを選択し、受信するメッセージと正確に一致できるように、それらのフィルターを構成することが重要です。 選択したフィルターの適合基準が幅広すぎる場合や、適切に構成されていない場合は、メッセージが正しくルーティングされません。 フィルターの適合基準が厳格すぎると、一部のメッセージの有効なルーティング先が見つからないことがあります。  
  
## <a name="filter-types"></a>フィルターの種類  
 ルーティング サービスで使用するフィルターを選択する際には、各フィルターのしくみと、受信メッセージの一部として使用できる情報について理解しておくことが重要です。 たとえば、すべてのメッセージが同じエンドポイントを介して受信される場合は、すべてのメッセージが Address フィルターと EndpointName フィルターに一致するため、これらのフィルターは役に立ちません。  
  
### <a name="action"></a>アクション  
 Action フィルターは <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> プロパティを確認します。 メッセージの Action ヘッダーの内容が、フィルター構成で指定されているフィルター データ値と一致する場合、このフィルターは `true` を返します。 次の例では、定義、`FilterElement`アクション フィルターを使用して、値を含むアクション ヘッダーを持つメッセージと一致する`http://namespace/contract/operation/`します。
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 一意のアクション ヘッダーを含むメッセージをルーティングするときは、このフィルターを使用する必要があります。  
  
### <a name="endpointaddress"></a>EndpointAddress  
 EndpointAddress フィルターは、メッセージを受信した EndpointAddress を確認します。 メッセージが着信したアドレスが、フィルター構成で指定されたフィルター アドレスと正確に一致した場合、このフィルターは `true` を返します。 次の例では、定義、`FilterElement`宛てのメッセージに一致するように、アドレス フィルターを使用する"http://\<ホスト名 >/vdir/s.svc/b"。  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  アドレスのホスト名部分は、クライアントで完全修飾ドメイン名、NetBIOS 名、IP アドレス、それ以外の名前のどれが使用されるかによって異なることがあります。 異なる値が同じホストを参照している場合があるため、この比較の既定の動作では、照合の際にアドレスのホスト名部分は使用されません。  
>   
>  ルーティング サービスをプログラムで構成する際に、比較の際にホスト名を評価できるように、この動作を変更できます。  
  
 受信メッセージが一意のアドレス宛てである場合は、このフィルターを使用する必要があります。  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 EndpointAddressPrefix フィルターは、EndpointAddress フィルターに似ています。 EndpointAddressPrefix フィルターは、メッセージを受信した EndpointAddress を確認します。 ただし、EndpointAddressPrefix フィルターは、フィルター構成で指定された値で始まるアドレスを一致させることによって、ワイルドカードとして機能します。 次の例では、定義、 `FilterElement` EndpointAddressPrefix フィルターを使用して、宛てのメッセージに一致する`http://<hostname>/vdir*`します。  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  アドレスのホスト名部分は、クライアントで完全修飾ドメイン名、NetBIOS 名、IP アドレス、それ以外の名前のどれが使用されるかによって異なることがあります。 異なる値が同じホストを参照している場合があるため、この比較の既定の動作では、照合の際にアドレスのホスト名部分は使用されません。  
  
 共通のアドレス プレフィックスを共有する受信メッセージをルーティングするときは、このフィルターを使用する必要があります。  
  
### <a name="and"></a>AND  
 AND フィルターが、メッセージ内の値を直接フィルターすることはありません。しかし、AND フィルターを使用すると、他の 2 つのフィルターを組み合わせて `AND` 条件を作成し、それらのフィルターの両方がメッセージと一致した場合に、AND フィルターが `true` に評価されるようにすることができます。 これにより、すべてのサブフィルターが一致した場合にだけ一致する、複雑なフィルターを作成できます。 次の例では、Address フィルターと Action フィルターを定義した後で、それらのフィルターの両方に照合してメッセージを評価する AND フィルターを定義します。 Address フィルターと Action フィルターの両方と一致した場合、AND フィルターは `true` を返します。  
  
```xml  
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>  
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);  
```  
  
 複数のフィルターのロジックを組み合わせて一致を判断する必要がある場合は、このフィルターを使用します。 たとえば、アクションとメッセージの特定の組み合わせだけを特定のアドレスに受け取る必要がある複数の送信先がある場合は、AND フィルターを使用して、必要な Action フィルターと Address フィルターを組み合わせることができます。  
  
### <a name="custom"></a>カスタム  
 カスタム フィルターの種類を選択する場合を含むアセンブリの型を含む customType 値を指定する必要があります、 **MessageFilter**このフィルターに使用する実装。 また、filterData には、Custom フィルターがメッセージの評価に必要とするすべての値が格納されている必要があります。 次の例では、`FilterElement` MessageFilter 実装を使用する `CustomAssembly.MyCustomMsgFilter` を定義します。  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 提供されるフィルターによってカバーされていないメッセージに対してカスタムの一致するロジックを実行する必要があるかどうかは[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]の実装であるカスタム フィルターを作成する必要があります、 **MessageFilter**クラス。 たとえば、受信メッセージ内の 1 つのフィールドを、構成としてフィルターに指定された既知の値のリストと比較するカスタム フィルターや、特定のメッセージ要素をハッシュしてから、その値を調査してフィルターが `true` と `false` のどちらを返すかを判断するカスタム フィルターを作成することができます。  
  
### <a name="endpointname"></a>EndpointName  
 EndpointName フィルターは、メッセージを受信したエンドポイントの名前を確認します。 次の例では、定義、 `FilterElement` SvcEndpoint で受信したメッセージをルーティングする EndpointName フィルターを使用します。  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 このフィルターは、ルーティング サービスが複数の名前付きサービス エンドポイントを公開する場合に役立ちます。 たとえば、ルーティング サービスがメッセージの受信に使用する 2 つのエンドポイントを公開し、その 1 つを、メッセージのリアルタイム処理を必要とする優先顧客が使用し、残りの 1 つを使用して、受信のタイミングが重要でないメッセージを受信する場合があります。  
  
 メッセージを受信したエンドポイントを特定する際に完全なアドレスの一致を使用することはよくありますが、定義されたエンドポイント名を使用すると、エラーの可能性が少なく、すばやく処理できるので便利です。特に、エンドポイント名が必須の属性となる、構成ファイルを使用したルーティング サービスの構成では、この方法が便利です。  
  
### <a name="matchall"></a>MatchAll  
 MatchAll フィルターは、受信したすべてのメッセージと一致します。 受信したすべてのメッセージのコピーを格納するログ サービスの場合など、受信したすべてのメッセージを常に特定のエンドポイントにルーティングする必要がある場合は、このフィルターが便利です。 次の例で定義する `FilterElement` では、MatchAll フィルターを使用します。  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 XPath フィルターを使用すると、XPath クエリを指定して、メッセージ内の特定の要素を確認できます。 XPath フィルターは、メッセージ内の XML アドレス指定可能なエントリを直接確認できる、強力なフィルター オプションです。ただし、このフィルターを使用するには、受信するメッセージの構造に関する特定の知識が必要です。 次の例では、定義、 `FilterElement` XPath フィルターを使用して、メッセージ"ns"の名前空間プレフィックスによって参照される名前空間内"の element"をという名前の要素を確認します。  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 受信するメッセージに特定の値が含まれていることがわかっている場合は、このフィルターが便利です。 たとえば、同じサービスの 2 つのバージョンをホストしており、そのサービスの新しい方のバージョン宛てのメッセージのカスタム ヘッダーに一意の値が含まれていることがわかっている場合は、XPath を使用するフィルターを作成してそのヘッダーに移動し、そのヘッダー内にある値を、フィルター構成で指定されている別の値と比較して、そのフィルターが一致するかどうかを判断できます。  
  
 XPath クエリには、長い文字列値または複雑な文字列値である一意の名前空間が含まれていることが多いため、XPath フィルターでは、名前空間用の一意のプレフィックスを定義する名前空間テーブルを使用できます。 名前空間のテーブルの詳細については、[メッセージ フィルター](../../../../docs/framework/wcf/feature-details/message-filters.md)を参照してください。  
  
 XPath クエリを設計する方法の詳細については、[XPath 構文](https://go.microsoft.com/fwlink/?LinkId=164592)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [メッセージ フィルター](../../../../docs/framework/wcf/feature-details/message-filters.md)
- [方法: フィルターを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
