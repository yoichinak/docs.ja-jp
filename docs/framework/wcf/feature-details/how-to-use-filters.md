---
title: '方法: フィルターの使用'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 5d3ed4a1d64edee274e60f5bf156b4294902df8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972862"
---
# <a name="how-to-use-filters"></a>方法: フィルターの使用
ここでは、複数のフィルターを使用したルーティング構成を作成するために必要な基本手順について説明します。 この例では、メッセージが、電卓サービスの 2 つの実装である regularCalc および roundingCalc にルーティングされます。 これらの実装は両方とも同じ操作をサポートしますが、片方のサービスでは、値を返す前にすべての計算を最も近い整数値に丸めます。 クライアント アプリケーションが、丸め処理を行うバージョンのサービスを使用するかどうかを表示可能である必要がありますが、優先するサービスが示されていない場合は、メッセージが 2 つのサービス間で負荷分散されます。 次の操作が両方のサービスによって公開されます。  
  
- 追加  
  
- 減算  
  
- 乗算  
  
- 除算  
  
 どちらのサービスも同じ操作を実装するため、アクション フィルターを使用することはできません。メッセージで指定されるアクションが一意にならないためです。 代わりに、メッセージが適切なエンドポイントに必ずルーティングされるための追加作業が必要になります。  
  
### <a name="determine-unique-data"></a>一意なデータを特定する  
  
1. 両方のサービス実装が同じ操作を処理し、返すデータを除いて基本的に同一であるため、クライアント アプリケーションから送信されるメッセージに含まれる基本データでは、要求をルーティングする方法を特定できません。 ただし、クライアント アプリケーションでメッセージに一意のヘッダー値を追加すると、この値を使用して、メッセージのルーティング方法を決定できます。  
  
     この例では、クライアント アプリケーションで丸め処理を行う電卓を使ってメッセージを処理する必要がある場合に、次のコードを使用してカスタム ヘッダーを追加します。  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     これで、XPath フィルターを使用して、メッセージにこのヘッダーが含まれるかどうかを確認し、このヘッダーを持つメッセージを roundCalc サービスにルーティングできるようになります。  
  
2. さらに、ルーティング サービスが、EndpointName、EndpointAddress、または PrefixEndpointAddress の各フィルターと共に使用できる仮想サービス エンドポイントを 2 つ公開し、クライアント アプリケーションの要求の送信先エンドポイントに基づいて、受信メッセージを特定の電卓の実装に一意にルーティングします。  
  
### <a name="define-endpoints"></a>エンドポイントを定義する  
  
1. ルーティング サービスで使用するエンドポイントを定義する場合は、最初にクライアントおよびサービスが使用するチャンネルの形状を決める必要があります。 このシナリオでは、両方の送信先サービスで要求/応答パターンが使用されるため、<xref:System.ServiceModel.Routing.IRequestReplyRouter> を使用します。 次の例では、ルーティング サービスが公開するサービス エンドポイントを定義します。  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     この構成では、ルーティング サービスは 3 つの別個のエンドポイントを公開します。 実行時の選択に応じて、クライアント アプリケーションは、これらのアドレスの 1 つにメッセージを送ります。 「仮想」サービスのエンドポイント ("丸め/calculator"または"標準/calculator") のいずれかに到着するメッセージは、対応する電卓の実装に転送されます。 クライアント アプリケーションが特定のエンドポイントに要求を送信しない場合、メッセージの送信先は標準のエンドポイントになります。 選択されたエンドポイントにかかわらず、クライアント アプリケーションでは、メッセージにカスタム ヘッダーを含めるように選択することで、丸め処理を行う電卓の実装にメッセージを転送するように指定することもできます。  
  
2. 次の例では、ルーティング サービスによるメッセージのルーティング先であるクライアント (送信先) エンドポイントを定義します。  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     これらのエンドポイントは、特定のフィルターと一致したメッセージの送信先エンドポイントを示すために、フィルター テーブルで使用されます。  
  
### <a name="define-filters"></a>フィルターを定義する  
  
1. クライアント アプリケーションがメッセージに追加"した RoundingCalculator"カスタム ヘッダーに基づいてメッセージをルーティングするには、XPath クエリを使用してこのヘッダーの存在を確認するフィルターを定義します。 このヘッダーは、カスタム名前空間を使用して定義されている、ため、また XPath クエリで使用される"custom"のカスタムの名前空間プレフィックスを定義する名前空間エントリを追加します。 次の例では、必要なルーティング セクション、名前空間のテーブル、および XPath フィルターを定義します。  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     これは、 **MessageFilter**は"rounding"という値を含むメッセージに RoundingCalculator ヘッダーを探します。 このヘッダーは、メッセージを roundingCalc サービスにルーティングする必要があることを示すために、クライアント側で設定されたものです。  
  
    > [!NOTE]
    > S12 の名前空間プレフィックスは既定では、名前空間テーブルに定義されているし、名前空間を表す`http://www.w3.org/2003/05/soap-envelope`します。
  
2. また、2 つの仮想エンドポイントで受信したメッセージがあるかどうかを検索するフィルターも定義する必要があります。 最初の仮想エンドポイントは、"通常/calculator"エンドポイントです。 クライアントは、メッセージを regularCalc サービスにルーティングする必要があることを示すために、このエンドポイントに要求を送信できます。 次の構成では、<xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> を使用するフィルターを定義して、filterData で指定された名前のエンドポイントでメッセージが受信されたかどうかを確認します。  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     このフィルターの評価が"calculatorEndpoint"という名前のサービス エンドポイントで、メッセージが受信した場合`true`します。  
  
3. 次に、roundingEndpoint のアドレスに送信されたメッセージがあるかどうかを検索するフィルターを定義します。 クライアントは、メッセージを roundingCalc サービスにルーティングする必要があることを示すために、このエンドポイントに要求を送信できます。 次の構成を使用するフィルターを定義する、 <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> "丸め/calculator"エンドポイントでメッセージが到着したかどうかを判断します。  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     始まるアドレスでメッセージを受信するかどうかは`http://localhost/routingservice/router/rounding/`にこのフィルターが評価されます**true**します。 この構成で使用されるベース アドレスである`http://localhost/routingservice/router`、roundingEndpoint"丸め/calculator"は、指定されたアドレス、このエンドポイントと通信するために使用する完全なアドレスは`http://localhost/routingservice/router/rounding/calculator`、このフィルターに一致します。  
  
    > [!NOTE]
    >  PrefixEndpointAddress フィルターは、一致するメッセージの確認を行う際にホスト名を評価しません。これは、1 つのホストへの参照を表す際に使用できるホスト名にはさまざまな種類があり、そのすべてが、クライアント アプリケーションからホストを参照するための正しい方法であるためです。 たとえば、次の例はすべて、同じホストを参照します。  
    >   
    > - localhost  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - ContosoWeb01  
  
4. 最後のフィルターでは、標準のエンドポイントで受信する、カスタム ヘッダーのないメッセージのルーティングがサポートされている必要があります。 このシナリオでは、regularCalc サービスと roundingCalc サービスで交互にメッセージが処理されます。 「ラウンド ロビン方式」のメッセージのルーティングをサポートするには、1 つのフィルター インスタンスを処理する各メッセージに一致するように、カスタム フィルターを使用します。  次のコードでは、RoundRobinMessageFilter のインスタンスを 2 つ定義します。これらは、交互に使用されることを示すために、グループ化されています。  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     実行中に、このフィルターの種類は、同じグループで 1 つのコレクションとして構成されている、この種類の定義済みフィルター インスタンスすべてを相次いで使用します。 これにより、交互にこのカスタム フィルターによって処理されるメッセージ`true`の`RoundRobinFilter1`と`RoundRobinFilter2`します。  
  
### <a name="define-filter-tables"></a>フィルター テーブルを定義する  
  
1. フィルターを特定のクライアント エンドポイントと関連付けるには、それぞれをフィルター テーブル内で指定する必要があります。 このサンプルのシナリオでは、フィルターの優先順位設定も使用しています。この設定は省略可能で、フィルターを処理する順序を指定できます。 優先順位を指定しない場合は、すべてのフィルターが同時に評価されます。  
  
    > [!NOTE]
    >  フィルターの優先順位を指定すると、フィルターが処理される順序を制御できますが、ルーティング サービスのパフォーマンスに影響を与える場合があります。 可能な場合は、フィルターの優先順位設定が不要になるようにフィルター ロジックを構築します。  
  
     次は、フィルター テーブルを定義し、2 の優先順位を持つテーブルに以前に定義された"XPathFilter"を追加します。 このエントリでは、その場合も指定します、 `XPathFilter` 、メッセージに一致、メッセージをルーティングするが、`roundingCalcEndpoint`します。  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     フィルターの優先順位を指定すると、優先順位の高いフィルターから評価されます。 指定された優先順位と一致するフィルターが 1 つまたは複数ある場合は、指定した優先順位より低いレベルのフィルターは評価されません。 ここでは、2 が、指定されている優先順位で最高であり、このレベルの唯一のフィルター エントリです。  
  
2. フィルター エントリは、メッセージが特定のエンドポイントで受信されているかどうかを、エンドポイント名またはアドレスのプレフィックスを調べることによって確認するために定義されています。 次のように入力することで、これらのフィルター エントリの両方をフィルター テーブルに追加し、メッセージがルーティングされる送信先エンドポイントに関連付けます。 前の XPath フィルターがメッセージと一致しない場合にのみ、これらのフィルターが実行されるようにするため、これらのフィルターの優先順位は 1 に設定されています。  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     優先順位が 1 に設定されているため、これらのフィルターは、優先順位が 2 に設定されているフィルターがメッセージと一致しない場合にのみ評価されます。 また、両方のフィルターに同じ優先順位が指定されているため、これらは同時に評価されます。 これらのフィルターは同時に指定できないため、いずれか一方だけがメッセージと一致する可能性があります。  
  
3. それまでのどのフィルターとも一致しないメッセージは、一般的なサービス エンドポイントを介して受信されており、ルーティング先を示すヘッダー情報が含まれていないメッセージです。 このようなメッセージはカスタム フィルターによって処理され、2 つの電卓サービス間で負荷分散されます。 次の例では、フィルター テーブルにフィルター エントリを追加する方法を示しています。各フィルターは、2 つの送信先エンドポイントのうちの 1 つに関連付けられます。  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     これらのエントリの優先順位は 0 に設定されているため、これらのフィルターは、優先順位が高いフィルターがメッセージと一致しない場合にのみ評価されます。 また、両方のフィルターに同じ優先順位が指定されているため、これらは同時に評価されます。  
  
     既に説明したように、これらのフィルター定義で使用されるカスタム フィルターは、受信するメッセージごとにどちらかのフィルターだけを `true` と評価します。 このフィルターを使用して定義されたフィルターは、同じグループ設定を持つ 2 つのフィルターのみであるため、ルーティング サービスが、regularCalcEndpoint と roundingCalcEndpoint に交互に送信するという効果をもたらします。  
  
4. メッセージをフィルターと照合して評価するには、最初に、フィルター テーブルをメッセージの受信に使用するサービス エンドポイントに関連付ける必要があります。  次の例は、ルーティング動作を使用して、ルーティング テーブルをサービス エンドポイントに関連付ける方法を示しています。  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>例  
 構成ファイル全体の一覧を次に示します。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ルーティング サービス](../../../../docs/framework/wcf/samples/routing-services.md)
