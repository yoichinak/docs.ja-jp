---
title: エンドポイントの作成の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 561839138baf448db881e3bd72777bda7b7c65bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941253"
---
# <a name="endpoint-creation-overview"></a>エンドポイントの作成の概要
Windows Communication Foundation (WCF) サービスとの通信はすべて、サービスの*エンドポイント*を介して行われます。 エンドポイントは、クライアントが WCF サービスによって提供される機能にアクセスできるようにします。 このセクションでは、エンドポイントの構造およびエンドポイントの設定またはコードによる定義の方法の概要を説明します。  
  
## <a name="the-structure-of-an-endpoint"></a>エンドポイントの構造  
 各エンドポイントは、そのエンドポイントが存在する場所を示すアドレス、クライアントがエンドポイントと通信するための方法を指定するバインディング、および利用可能なメソッドを特定するコントラクトで構成されます。  
  
- **アドレス**。 アドレスは、エンドポイントを一意に識別し、潜在的なユーザーにそのサービスの場所を示します。 これは、WCF オブジェクトモデルでは、 <xref:System.ServiceModel.EndpointAddress>アドレスによって表されます。これには、id、Web サービス記述言語 (WSDL) 要素、および省略可能なコレクションを含む Uniform Resource Identifier (URI) とアドレスのプロパティが含まれます。ヘッダー. オプション ヘッダーは、エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。 詳細については、「[エンドポイントアドレスの指定](../../../docs/framework/wcf/specifying-an-endpoint-address.md)」を参照してください。  
  
- **バインド**。 バインディングはエンドポイントとの通信方法を指定します。 バインディングによって、使用するトランスポート プロトコル (TCP や HTTP など)、メッセージに使用するエンコード (テキストやバイナリなど)、必要なセキュリティ要件 (SSL (Secure Sockets Layer) や SOAP メッセージ セキュリティなど) など、そのエンドポイントが通信を行う方法が指定されます。 詳細については、「バインディングを使用した[サービスとクライアントの構成](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)」を参照してください。  
  
- **サービスコントラクト**。 サービス コントラクトは、エンドポイントがクライアントに公開する機能を示します。 コントラクトは、クライアントが呼び出すことのできる操作、メッセージの形式、操作の呼び出しに必要な入力パラメーターやデータの型、クライアントに提供する処理または応答メッセージの種類を指定します。 基本的なメッセージ交換パターン (MEP) に対応する基本的なコントラクトの種類には、データグラム (一方向)、要求/応答、二重 (双方向) の 3 つがあります。 サービス コントラクトは、データ コントラクトとメッセージ コントラクトを使用して、クライアントが特定のデータ型とメッセージ形式でアクセスするように要求することもできます。 サービスコントラクトを定義する方法の詳細については、「[サービスコントラクトの設計](../../../docs/framework/wcf/designing-service-contracts.md)」を参照してください。 クライアントでは、二重 MEP でサービスからメッセージを受信するために、コールバック コントラクトというサービス定義のコントラクトを実装することが必要な場合があります。 詳細については、「[双方向サービス](../../../docs/framework/wcf/feature-details/duplex-services.md)」を参照してください。  
  
 サービスのエンドポイントはコードを使用して強制的に指定するか、構成を介して宣言として指定できます。 エンドポイントが指定されていない場合、ランタイムは、サービスで実装されたサービス コントラクトごとに、1 つの既定のエンドポイントを各ベース アドレスに追加することで、既定のエンドポイントを提供します。 設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。 一般に、サービス エンドポイントの定義にはコードではなく、構成を使用する方がより実用的です。 バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。  
  
> [!NOTE]
> 偽装を行うサービス エンドポイントを追加する場合は、<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドまたは <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> メソッドのいずれかを使用して、コントラクトを新しい <xref:System.ServiceModel.Description.ServiceDescription> オブジェクトに適切に読み込む必要があります。  
  
## <a name="defining-endpoints-in-code"></a>コードでのエンドポイントの定義  
 次の例は、コードにエンドポイントを指定する方法を示しています。  
  
- 任意の名前を受け付け、"Hello \<name>!" とエコー応答するサービスの `IEcho` 型のコントラクトを定義します。  
  
- `Echo` コントラクトで定義された型の `IEcho` サービスを実装します。  
  
- サービスのエンドポイントアドレス`http://localhost:8000/Echo`を指定します。  
  
- <xref:System.ServiceModel.WSHttpBinding> のバインディングを使用して `Echo` サービスを構成します。  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
> サービス ホストはベース アドレスを使用して作成されます。また、残りのアドレス (ベース アドレスの相対アドレス) はエンドポイントの一部として指定されます。 このようにアドレスを分割することで、ホストのサービスで複数のエンドポイントを簡単に定義できるようになります。  
  
> [!NOTE]
> <xref:System.ServiceModel.Description.ServiceDescription> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> メソッドの後で、サービス アプリケーションの <xref:System.ServiceModel.ServiceHostBase> の各プロパティを変更しないでください。 このメソッドの後で変更すると、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> および `AddServiceEndpoint` の <xref:System.ServiceModel.ServiceHostBase> プロパティや <xref:System.ServiceModel.ServiceHost> メソッドなどの一部のメンバーは例外をスローします。 変更を許可するメンバーもありますが、結果は未定義の状態になります。  
>   
>  同様に、クライアントで、<xref:System.ServiceModel.Description.ServiceEndpoint> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 呼び出しの後で、<xref:System.ServiceModel.ChannelFactory> 値を変更しないでください。 この呼び出しの後で変更すると、<xref:System.ServiceModel.ChannelFactory.Credentials%2A> プロパティは例外をスローします。 その他のクライアント記述値は、エラーを発生させずに変更できますが、結果は未定義の状態になります。  
>   
>  サービスとクライアントのどちらの場合も、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> の呼び出しの前に記述を変更することをお勧めします。  
  
## <a name="defining-endpoints-in-configuration"></a>構成でのエンドポイントの定義  
 アプリケーションの作成では、各種決定事項をアプリケーションを展開する管理者に任せる場合がよくあります。 たとえば、どのサービス アドレス (URI) を使用するかなどの情報は、前もって知るすべがありません。 アドレスをハードコーディングする代わりに、サービスの作成後に管理者が指定する方が便利です。 構成を活用することで、この柔軟性が得られます。 詳細については、[サービスを構成する](../../../docs/framework/wcf/configuring-services.md) を参照してください。  
  
> [!NOTE]
> [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) の `/config:`*filename*`[,`*filename*`]` を切り替えて使用すると、構成ファイルをすばやく作成できます。  
  
## <a name="using-default-endpoints"></a>既定のエンドポイントの使用  
 エンドポイントがコードまたは構成で指定されていない場合、ランタイムは、サービスで実装されたサービス コントラクトごとに、1 つの既定のエンドポイントを各ベース アドレスに追加することで、既定のエンドポイントを提供します。 ベース アドレスはコードまたは構成で指定することができ、既定のエンドポイントは、<xref:System.ServiceModel.ICommunicationObject.Open> が <xref:System.ServiceModel.ServiceHost> で呼び出されるときに追加されます。 次の例は上記のセクションの例と同じです。ただし、エンドポイントを指定せず、既定のエンドポイントを追加する点が異なります。  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 エンドポイントを明示的に指定しない場合、<xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> を呼び出す前に、<xref:System.ServiceModel.ServiceHost> で <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> を呼び出すことによって、既定のエンドポイントを引き続き追加できます。 既定のエンドポイントの詳細については、「 [WCF サービスの](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../docs/framework/wcf/simplified-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)
