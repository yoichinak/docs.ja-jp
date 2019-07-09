---
title: 開発者の視点から見た ASP.NET Web サービスと WCF との比較
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: 8b0e26f0b76ee56d06c426cd3c11b169a74b1896
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663370"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>開発者の視点から見た ASP.NET Web サービスと WCF との比較

Windows Communication Foundation (WCF) では、WCF アプリケーションのプログラミングし、ASP.NET Web サービスのように構成を有効にして、その動作を模倣する ASP.NET 互換性モード オプションがあります。 次のセクションでは、ASP.NET Web サービスの比較され、WCF が両方のテクノロジを使用してアプリケーションの開発に必要なものに基づきます。

## <a name="data-representation"></a>データ表現

ASP.NET で Web サービスを開発する場合、通常はまず、このサービスが使う複合データ型の定義から始めます。 ASP.NET は <xref:System.Xml.Serialization.XmlSerializer> を利用して、.NET Framework 型で表されたデータを XML 形式に変換してサービスとの間でやり取りしたり、XML 形式で受け取ったデータを .NET Framework オブジェクトに変換したりします。 ASP.NET サービスで使用する複合データ型を定義するには、<xref:System.Xml.Serialization.XmlSerializer> で XML 形式にシリアル化したり、XML 形式から逆シリアル化したりできる .NET Framework クラスの定義が必要です。 クラス定義は手で記述するほか、XML スキーマの型定義から生成することも可能です。それにはコマンド ライン上で実行する XML スキーマ/データ型サポート ユーティリティである xsd.exe を使います。

<xref:System.Xml.Serialization.XmlSerializer> で XML 形式にシリアル化したり、XML 形式から逆シリアル化したりできる .NET Framework クラスを定義する場合に知っておくべき主な事項を次に示します。

- XML に変換されるのは、.NET Framework オブジェクトのパブリック フィールドおよびパブリック プロパティに限ります。

- コレクション クラスのインスタンスを XML 形式にシリアル化できるのは、そのクラスが <xref:System.Collections.IEnumerable> または <xref:System.Collections.ICollection> インターフェイスを実装している場合に限ります。

- <xref:System.Collections.IDictionary> インターフェイスを実装した、<xref:System.Collections.Hashtable> などのクラスを、XML 形式にシリアル化することはできません。

- <xref:System.Xml.Serialization> 名前空間の属性型は、大部分が .NET Framework クラスやそのメンバーに追加可能であり、これにより、XML での当該クラスのインスタンスの表現方法を制御できます。

通常、WCF アプリケーションの開発は複合型の定義を含むもが開始します。 WCF は、ASP.NET Web サービスと同じ .NET Framework 型を使用して作成できます。

WCF<xref:System.Runtime.Serialization.DataContractAttribute>と<xref:System.Runtime.Serialization.DataMemberAttribute>型のインスタンスを XML、およびどの特定のフィールドまたは型のプロパティをシリアル化する、次のサンプル コードに示すようにシリアル化することを示す .NET Framework 型に追加することができます。

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

<xref:System.Runtime.Serialization.DataContractAttribute> は、当該型の中にシリアル化可能なフィールドやプロパティがあることを示し、具体的にどのフィールドやプロパティをシリアル化できるかを <xref:System.Runtime.Serialization.DataMemberAttribute> で示します。 <xref:System.Runtime.Serialization.DataContractAttribute> はクラスにも構造体にも適用できます。 <xref:System.Runtime.Serialization.DataMemberAttribute> はフィールドやプロパティに適用します。これはパブリックでもプライベートでもかまいません。 型のインスタンス、<xref:System.Runtime.Serialization.DataContractAttribute>に適用されるにと呼ばれる WCF でのデータ コントラクトします。 これを XML 形式にシリアル化するには <xref:System.Runtime.Serialization.DataContractSerializer> を使います。

<xref:System.Runtime.Serialization.DataContractSerializer> を使う場合と、<xref:System.Xml.Serialization.XmlSerializer> および <xref:System.Xml.Serialization> 名前空間に定義された属性を使う場合の、主な違いを以下に示します。

- <xref:System.Xml.Serialization.XmlSerializer> や <xref:System.Xml.Serialization> 名前空間の属性は、XML スキーマで定義された有効な型であればどれにでも .NET Framework 型をマップできるようにするためのものです。これらを使うと、XML での型の表現方法を細かく制御できます。 これに対し、<xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.DataContractAttribute>、および <xref:System.Runtime.Serialization.DataMemberAttribute> の場合、XML での型の表現方法にはほとんど自由度がありません。 指定できるのは、名前空間と、型やフィールド、プロパティを XML で表す名前、フィールドやプロパティの XML における並び順だけです。

  ```csharp
  [DataContract(
  Namespace="urn:Contoso:2006:January:29",
  Name="LineItem")]
  public class LineItem
  {
        [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
        public string itemNumber;
        [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
        public decimal quantity;
        [DataMember(Name="Price",IsRequired=false,Order = 2)]
        public decimal unitPrice;
  }
  ```

  上記以外の事項は、<xref:System.Runtime.Serialization.DataContractSerializer> に固定で組み込まれています。

- <xref:System.Runtime.Serialization.DataContractSerializer> の場合、型の XML での表現方法に自由度が小さく、したがってシリアル化のプロセスがあらかじめ大部分予測できるので、最適化が容易です。 <xref:System.Runtime.Serialization.DataContractSerializer> を使えば、性能が約 10% 向上するという現実的な利点があります。

- <xref:System.Xml.Serialization.XmlSerializer> を使用する方法では、どのフィールドやプロパティを XML にシリアル化するかを属性で指定することはできませんが、<xref:System.Runtime.Serialization.DataMemberAttribute> の場合は <xref:System.Runtime.Serialization.DataContractSerializer> 属性で明示的に指定できます。 このように、データ コントラクトとは、アプリケーションとの間でやり取りするデータ構造を明示した契約であると言うことができます。

- <xref:System.Xml.Serialization.XmlSerializer> で XML 形式に変換できるのは、.NET オブジェクトのパブリック メンバーに限ります。一方 <xref:System.Runtime.Serialization.DataContractSerializer> は、アクセス修飾子にかかわらず、どのメンバーでも変換可能です。

- <xref:System.Runtime.Serialization.DataContractSerializer> の場合、パブリックでないメンバーも XML に変換できるため、シリアル化できる .NET 型についての制約が少なくなります。 特に、<xref:System.Collections.Hashtable> など、<xref:System.Collections.IDictionary> インターフェイスを実装した型が変換可能です。 <xref:System.Runtime.Serialization.DataContractSerializer> はさらに、既存の .NET 型のインスタンスを XML にシリアル化する場合でも、型定義を変更したり、ラッパーを定義したりする必要がありません。

- <xref:System.Runtime.Serialization.DataContractSerializer> はパブリックでないメンバーも変換できるため、完全に信頼できるコードからしか実行できないようになっています。<xref:System.Xml.Serialization.XmlSerializer> にはそのような制約がありません。 コードの完全な信頼アクセス許可は、コードが実行されている資格情報を使用してアクセスできるコンピューター上のすべてのリソースへの完全なアクセスを示します。 このオプションは、完全に信頼されたコード、コンピューター上のすべてのリソースにアクセスするように注意して使用する必要があります。

- <xref:System.Runtime.Serialization.DataContractSerializer> にはバージョン管理の機能がいくつか組み込まれています。

  - <xref:System.Runtime.Serialization.DataMemberAttribute> には <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> プロパティがあります。旧バージョンにはなかったメンバーを追加した場合に、そのプロパティを false とすれば、当該データ コントラクトの新バージョンを扱うアプリケーションが、旧バージョンのデータも扱えるようになります。

  - データ コントラクトに <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装すると、<xref:System.Runtime.Serialization.DataContractSerializer> は、新バージョンのデータ コントラクトで定義されたメンバーを、旧バージョンのコントラクトを扱うアプリケーション経由で受け渡しできるようになります。

以上のようにさまざまな違いがありますが、<xref:System.Xml.Serialization.XmlSerializer> で既定の設定を使用して型をシリアル化したものは、XML の名前空間を明示的に定義してあれば、<xref:System.Runtime.Serialization.DataContractSerializer> で型をシリアル化したものと意味的に同等です。 シリアライザーの両方で使用するための属性を持ち、次のクラスは、意味的に同一の XML に変換されます、<xref:System.Xml.Serialization.XmlSerializer>および、 <xref:System.Runtime.Serialization.DataContractAttribute>:

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

Windows ソフトウェア開発キット (SDK) と呼ばれるコマンド ライン ツールが含まれています、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。 などの xsd.exe ツールは、ASP.NET Web サービスで使用される、Svcutil.exe は、XML スキーマから .NET データ型の定義を生成できます。 <xref:System.Runtime.Serialization.DataContractSerializer> が XML スキーマで定義された形式の XML を出力できる場合、型はデータ コントラクトの形に変換されます。そうでなければ、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化します。 Svcutil.exe を使用してデータ コントラクトから XML スキーマも生成できるその`dataContractOnly`スイッチします。

> [!NOTE]
> ASP.NET Web サービスの使用、 <xref:System.Xml.Serialization.XmlSerializer>、および WCF の ASP.NET 互換モードは、ASP.NET Web サービスの動作を模倣する WCF サービス、ASP.NET 互換性オプションも使用する 1 つは制限されません、<xref:System.Xml.Serialization.XmlSerializer>します。 必要であれば ASP.NET 互換モードでも <xref:System.Runtime.Serialization.DataContractSerializer> も使えるようになっています。

## <a name="service-development"></a>サービスの開発

ASP.NET を使用してサービスを開発する場合、通常は <xref:System.Web.Services.WebService> 属性をクラスに追加し、<xref:System.Web.Services.WebMethodAttribute> を当該クラスのサービスに対する操作メソッドに追加します。

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

ASP.NET 2.0 では、<xref:System.Web.Services.WebService> 属性や <xref:System.Web.Services.WebMethodAttribute> 属性をクラスではなくインターフェイスに追加し、そのインターフェイスを実装するクラスを記述する、という方法も使えるようになりました。

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

<xref:System.Web.Services.WebService> 属性を持つインターフェイスは、サービスによって実行される操作のコントラクトを構成し、またそれをさまざまなクラスで再利用することによって、同じコントラクトをさまざまな方法で実装できるので、このオプションの使用をお勧めします。

WCF サービスは、1 つまたは複数の WCF エンドポイントの定義によって提供されます。 エンドポイントは、アドレス、バインディング、サービス コントラクトで定義します。 アドレスとは、サービスが配備された場所のことです。 バインディングはサービスとの通信方法を表します。 サービス コントラクトとは、サービスが実行できる操作の定義のことです。

サービス コントラクトは通常、インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> および <xref:System.ServiceModel.OperationContractAttribute> を追加して定義します。

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<xref:System.ServiceModel.ServiceContractAttribute>インターフェイスは、WCF サービス コントラクトを定義することを指定します、 <xref:System.ServiceModel.OperationContractAttribute> 、あれば、インターフェイスのメソッドの定義するサービス コントラクトの操作を示します。

このようにして定義されたサービス コントラクトをクラスとして実装します。サービス コントラクトを定義するインターフェイスを実装するクラスという形で記述します。

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

サービス コントラクトを実装するクラスは、WCF での入力をサービスとして参照されます。

次に、アドレスとバインディングを、サービス型と関連付けます。 通常、直接、ファイルを編集して、または WCF で提供される構成エディターを使用して、構成ファイルで行われます。 構成ファイルの例を以下に示します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

バインディングは、アプリケーションとの通信に使う一連のプロトコルを表します。 一般的なシステム指定のバインディングを以下に示します。

|名前|目的|
|----------|-------------|
|BasicHttpBinding|WS-BasicProfile 1.1 および Basic Security Profile 1.0 に対応した Web サービスやクライアントとの相互運用性。|
|WSHttpBinding|HTTP 上の WS-* プロトコルに対応した Web サービスやクライアントとの相互運用性。|
|WSDualHttpBinding|双方向 HTTP 通信。最初のメッセージの受信者は送信元に直接は応答せず、代わりに、WS-* プロトコルに準拠した HTTP で、ある期間にわたって任意の数の応答を送信することができます。|
|WSFederationBinding|HTTP 通信。サービスのリソースに対するアクセスを、明示的に指定された資格情報プロバイダーによって発行された証明書に基づいて制御することができます。|
|NetTcpBinding|ネットワーク経由で WCF ソフトウェア エンティティ間の通信のセキュリティで保護された、信頼性の高い、高パフォーマンス|
|NetNamedPipeBinding|同じコンピューターに WCF ソフトウェア エンティティ間の通信のセキュリティで保護された、信頼性の高い、高パフォーマンス|
|NetMsmqBinding|MSMQ を使用して WCF ソフトウェア エンティティ間の通信。|
|MsmqIntegrationBinding|WCF のソフトウェア エンティティと MSMQ を使用して別のソフトウェア エンティティ間の通信。|
|NetPeerTcpBinding|Windows ピア ツー ピア ネットワー キングを使用して WCF ソフトウェア エンティティ間の通信。|

システム指定のバインディングである <xref:System.ServiceModel.BasicHttpBinding> には、ASP.NET Web サービスが対応している一連のプロトコルが組み込まれています。

WCF アプリケーションのカスタム バインドは、WCF を使用して個々 のプロトコルを実装するバインド要素クラスのコレクションとして簡単に定義されます。 追加のプロトコルを表す、新しいバインド要素を記述することも可能です。

サービス型の内部的な動作は、動作を表すクラス群のプロパティで調整できます。 次の例で、<xref:System.ServiceModel.ServiceBehaviorAttribute> クラスは、サービス型がマルチスレッド処理されることを指定しています。

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<xref:System.ServiceModel.ServiceBehaviorAttribute> など、属性として定義された動作もあります。 これに対し、管理者がプロパティを設定できる動作は、アプリケーションの構成ファイルで変更することができます。

サービス型のプログラムの記述には、多くの場合 <xref:System.ServiceModel.OperationContext> クラスを使います。 静的プロパティである <xref:System.ServiceModel.OperationContext.Current%2A> を介して、実行コンテキストに関する情報にアクセスできます。 <xref:System.ServiceModel.OperationContext> の使い方は、<xref:System.Web.HttpContext> クラスや <xref:System.EnterpriseServices.ContextUtil> クラスと同様です。

## <a name="hosting"></a>ホスト

ASP.NET Web サービスは、コンパイルしてクラス ライブラリ アセンブリの形になっています。 サービス ファイルという、拡張子が .asmx のファイルの `@ WebService` ディレクティブに、サービスの実行コードが組み込まれたクラスと、これを収容するアセンブリが定義されています。

```
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>
```

サービス ファイルをインターネット インフォメーション サービス (IIS) の ASP.NET アプリケーション ルート、アセンブリをアプリケーション ルートのサブディレクトリ \bin 以下にコピーすると、 このサービス ファイルの URL (Uniform Resource Locator) でアプリケーションにアクセスできるようになります。

および任意の .NET アプリケーション内で IIS 5.1 または 6.0 では、Windows プロセス アクティブ化サービス (WAS) IIS 7.0 の一部として提供されている WCF サービスをホストに容易にできます。 ただし IIS 5.1/6.0 の場合、通信トランスポート プロトコルは HTTP に限ります。

IIS 5.1/6.0 または WAS 上でサービスをホストする手順を以下に示します。

1. サービス型をコンパイルしてクラス ライブラリ アセンブリを生成します。

2. 拡張子を .svc としたサービス ファイルを作り、サービス型を `@ ServiceHost` ディレクティブで次のように指定します。

    ```
    <%@ServiceHost language="c#" Service="MyService" %>
    ```

3. サービス ファイルを仮想ディレクトリにコピーし、アセンブリをその仮想ディレクトリの \bin サブディレクトリにコピーします。

4. 構成ファイルを仮想ディレクトリに、Web.config という名前でコピーします。

するとアプリケーションには、アプリケーション ルートに置いたサービス ファイルの URL でアクセスできるようになります。

.NET アプリケーション内で WCF サービスをホストするサービス型、アプリケーションによって参照されるクラス ライブラリ アセンブリをコンパイルし、サービスを使用して、ホストにアプリケーションをプログラミング、<xref:System.ServiceModel.ServiceHost>クラス。 サービスを管理する基本的なプログラムの例を以下に示します。

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

この例では <xref:System.ServiceModel.ServiceHost> の構築時にトランスポート プロトコルに対してアドレスを指定しています。 このアドレスをベース アドレスと呼びます。

WCF サービスのエンドポイントに指定されたアドレスは、エンドポイントのホストのベース アドレスに対する相対アドレスです。 ホストではトランスポート プロトコルごとに 1 つベース アドレスを設定できます。 上記の構成ファイルの構成例では、エンドポイントに対して選択された <xref:System.ServiceModel.BasicHttpBinding> はトランスポート プロトコルとして HTTP を使用しているので、エンドポイント `EchoService` のアドレスは、HTTP に対して設定されたベース アドレスを基準としたものになります。 上記の例では、ホストの場合、HTTP ベース アドレスは`http://www.contoso.com:8000/`します。 なお、IIS や WAS 上でホストされているサービスの場合、ベース アドレスはサービス ファイルの URL になります。

WCF の ASP.NET 互換モード オプションを使用する IIS または WAS とする構成と HTTP トランスポート プロトコルとして排他的でホストされているサービスのみが可能です。 ASP.NET 互換モードは、次の 2 つの手順で切り替えます。

1. プログラムの開発者は、サービス型に <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 属性を追加し、ASP.NET 互換モードに切り替えることができる、または切り替えることが必須である旨の指定をしておく必要があります。

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. 管理者は、アプリケーションが ASP.NET 互換モードで動作するよう、次のように構成する必要があります。

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    WCF アプリケーションを構成すると、.svc ではなく、サービス ファイルの拡張機能として .asmx を使用することもできます。

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    オプションでは、WCF を使用するサービスを変更する場合に .asmx サービス ファイルの Url を使用するように構成されたクライアントを変更することから保存できます。

## <a name="client-development"></a>クライアント開発

ASP.NET Web サービスのクライアントの開発にはコマンド ライン ツール WSDL.exe を使用します.asmx ファイルの URL を入力として指定します。 WCF に用意された、対応するツールが[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。 サービス コントラクトの定義と WCF クライアント クラスの定義を持つコード モジュールを生成します。 また、サービスのアドレスとバインディングを指定して、構成ファイルを生成することもできます。

リモート サービスのクライアントを開発する場合、通常は、非同期パターンに従ってプログラムを記述するようお勧めします。 WSDL.exe ツールは、特段の指定をしなくても、同期パターンと非同期パターンを使ったコードをそれぞれ生成します。 によって生成されたコード、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)のいずれかのパターンを指定できます。 特に指定しなければ同期パターン用です。 `/async` スイッチを指定して実行すれば、生成されるコードは非同期パターン用になります。

ASP によって生成された WCF クライアント クラスの名前を示す保証はありません。NET の WSDL.exe ツールでは、既定では、Svcutil.exe ツールによって生成された WCF クライアント クラスの名前と一致します。 特に、<xref:System.Xml.Serialization.XmlSerializer> でシリアル化したクラスのプロパティ名は、Svcutil.exe で生成した場合 "Property" という接頭辞が付きますが、WSDL.exe の場合はそうなりません。

## <a name="message-representation"></a>メッセージ表現

ASP.NET Web サービスとやり取りする SOAP メッセージのヘッダーはカスタマイズ可能です。 <xref:System.Web.Services.Protocols.SoapHeader> の派生クラスでヘッダーの構造を定義し、<xref:System.Web.Services.Protocols.SoapHeaderAttribute> でヘッダーが存在することを指定します。

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

WCF は、属性を提供<xref:System.ServiceModel.MessageContractAttribute>、<xref:System.ServiceModel.MessageHeaderAttribute>と<xref:System.ServiceModel.MessageBodyMemberAttribute>サービスによって送受信される SOAP メッセージの構造を記述します。

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

この構文でメッセージ構造を明示的に記述できますが、ASP.NET Web サービスのコードからメッセージ構造を導くことも可能です。 また、ASP.NET の構文ではメッセージ ヘッダーとして表されます、サービスのプロパティなど、`ProtocolHeader`前の例では、プロパティが WCF の構文ではメッセージのプロパティとしてより正確に表されます。 また、WCF では、エンドポイントの構成に追加するメッセージ ヘッダーができます。

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

この方法では、クライアントやサービスのコード内で、基盤となるプロトコル ヘッダーを参照しなくても済みます。エンドポイントが適切に構成されているので、ヘッダーがメッセージ中に取り込まれるからです。

## <a name="service-description"></a>サービスの説明

WSDL で記述したクエリを HTTP GET 要求として発行して、ASP.NET Web サービスの .asmx ファイルを取得しようとすると、ASP.NET は WSDL によるサービス記述を生成し、 要求に対する応答として返します。

ASP.NET 2.0 では、サービスが Web Services-Interoperability Organization (WS-I) の Basic Profile 1.1 に準拠していることを検証し、その旨を WSDL による記述に追加できるようになりました。 この処理には、`ConformsTo` 属性の `EmitConformanceClaims` および <xref:System.Web.Services.WebServiceBindingAttribute> パラメーターを使用します。

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

ASP.NET が WSDL で生成したサービス記述はカスタマイズ可能です。 <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> の派生クラスを作成し、WSDL による記述に項目を追加する、という形でカスタマイズします。

WCF でサービスを記述する WSDL 応答は、IIS 51 内でホストされている HTTP エンドポイントを持つクエリは、WSDL、WCF サービスの .svc ファイルの HTTP GET 要求を発行する 6.0 または WAS から発生します。 httpGetEnabled が true に設定されている場合は、WSDL で記述したクエリを HTTP GET 要求として、.NET アプリケーション上でホストされているサービスの HTTP ベース アドレスに発行しても同じ効力があります。

ただし、WCF は、サービスの記述を生成すると、WSDL での Ws-metadataexchange 要求にも応答します。 ASP.NET Web サービスには、WS-MetadataExchange 要求に応答する機能がありません。

WCF によって生成される WSDL を広範囲にカスタマイズできます。 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスには、WSDL による記述をカスタマイズするための機能がいくつか組み込まれています。 WSDL を生成しませんが、静的な WSDL ファイルを使用して、特定の url にではなく、WCF を構成することもできます。

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a>例外処理

ASP.NET Web サービスでは、処理できない例外が発生すると、SOAP エラーとしてクライアントに返されます。 また、<xref:System.Web.Services.Protocols.SoapException> クラスのインスタンスを明示的にスローして、クライアント側に SOAP エラーの詳しい状況を通知し、より適切に管理させることも可能です。

WCF サービスで未処理の例外は返されませんをクライアントに機密情報が、例外を誤って公開されることを防ぐために SOAP エラーとして。 ただしデバッグ目的で、このような例外をクライアントに返すように設定することは可能です。

SOAP エラーをクライアントに返す場合、データ コントラクト型を汎用型 <xref:System.ServiceModel.FaultException%601> のインスタンスとしてキャストし、これをスローする方法が使えます。 また、操作に <xref:System.ServiceModel.FaultContractAttribute> 属性を追加して、操作で生じうるエラーを指定する方法もあります。

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

これにより、サービスで発生する可能性のあるエラーが WSDL の形で公開されます。クライアント側の開発者は、当該操作によりどのようなエラーが生じうるかをあらかじめ予測し、catch ブロック内に適切な処理を組み込んでおくことができます。

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a>状態管理

ASP.NET Web サービスの実装には <xref:System.Web.Services.WebService> の派生クラスを使うこともできます。

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

この場合、基本クラス <xref:System.Web.Services.WebService> に定義された Context プロパティを使って、<xref:System.Web.HttpContext> オブジェクトにアクセスすることになります。 <xref:System.Web.HttpContext> オブジェクトには、アプリケーションやセッションの状態情報をそれぞれ更新、取得する、Application プロパティ、Session プロパティがあります。

ASP.NET では、<xref:System.Web.HttpContext> の Session プロパティでアクセスするセッション状態情報の、実際の格納場所を細かく制御できます。 格納場所としては、クッキー内、データベース内、稼動中のサーバーのメモリ上、状態管理用の特別なサーバーのメモリ上があり、 サービスの構成ファイルで指定します。

WCF では、状態管理の拡張可能なオブジェクトを提供します。 いずれも <xref:System.ServiceModel.IExtensibleObject%601> を実装しています。 中でも重要な拡張可能オブジェクトは、<xref:System.ServiceModel.ServiceHostBase> および <xref:System.ServiceModel.InstanceContext> です。 `ServiceHostBase` を使用すると、同一ホスト上の全サービス型のあらゆるインスタンスからアクセスできる状態を管理できます。一方、`InstanceContext` を使用すると、同じサービス型のインスタンス内で実行されるコードからアクセスできる状態を管理できます。

ここでは、サービスの種類、`TradingSystem`が、<xref:System.ServiceModel.ServiceBehaviorAttribute>同じ WCF クライアント インスタンスからのすべての呼び出しは、サービスの種類の同じインスタンスにルーティングされますを指定します。

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

次のクラス `DealData` に定義されている状態には、同じサービス型のインスタンス内で実行されるどのコードからでもアクセスできます。

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

サービス コントラクトの操作のいずれかを実装するサービス型のコードでは、状態オブジェクト `DealData` を、当該サービス型の現在のインスタンスに関する状態として追加することができます。

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

この状態オブジェクトは、サービス コントラクトの他の操作を実装するコードから取得、更新できます。

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

ASP.NET では、経由でコントロールが用意されていますが、状態の情報、<xref:System.Web.HttpContext>クラスが実際に格納されている WCF では、少なくとも、初期のバージョンでは拡張可能なオブジェクトを格納する場所を細かく制御します。 WCF サービスの ASP.NET 互換モードを選択するため、推奨する理由を構成します。 このような制御が不可欠な応用の場合、ASP.NET 互換モードにすれば、ASP.NET と同様に <xref:System.Web.HttpContext> クラスの機能を活用できるばかりでなく、<xref:System.Web.HttpContext> クラスで管理する状態情報の実際の格納場所も制御できます。

## <a name="security"></a>セキュリティ

ASP.NET Web サービスのセキュリティ保全の手順は、IIS アプリケーションのセキュリティ保全の手順と同じです。 IIS 内でだけでなく、任意の .NET 実行可能ファイル内でも、WCF アプリケーションをホストできるため、WCF アプリケーションをセキュリティで保護するためのオプションに IIS の機能から独立して行う必要があります。 ただし、ASP.NET Web サービスを提供する機能では、ASP.NET 互換モードで実行されている WCF サービスを入手できます。

### <a name="security-authentication"></a>セキュリティ:認証

IIS は、匿名アクセスまたはさまざまな認証のモードのいずれかを選択する、アプリケーションへのアクセスを制御するための機能を提供します。Windows 認証、ダイジェスト認証、基本認証、および .NET Passport 認証します。 Windows 認証は、ASP.NET Web サービスへのアクセス制御に使えます。 ただし、WCF アプリケーションが IIS 内でホストされているときに、さまざまなその他のオプション間での Windows 認証をサポートして、WCF によって、その認証を管理できるように、アプリケーションへの匿名アクセスを許可するように IIS を構成する必要があります。 他の認証方法としては、ユーザー名トークン、X.509 証明書、SAML トークン、CardSpace カードなどが組み込まれていますが、独自の認証機構を定義することも可能です。

### <a name="security-impersonation"></a>セキュリティ:偽装

ASP.NET Web サービスは ASP.NET の ID 要素を使用して、あるユーザーに偽装することができます。あらかじめ設定した特定のユーザーでなくても、要求に資格情報が添えられていれば、その要求元ユーザーに偽装できます。 ASP.NET 互換モードで実行されている WCF アプリケーションで偽装を構成するのには、その要素を使用できます。

WCF 構成システムは、特定の権限を借用するユーザーを指定するため、独自の id 要素を提供します。 また、WCF クライアントおよびサービス別に構成できます権限借用のため。 クライアント側では、要求を送信する現在のユーザーに偽装する構成が可能です。

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

サービス側では、現在の要求と共に提供された資格情報のユーザーに偽装するように構成できます。

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a>セキュリティ:アクセス制御リストを使用した承認

アクセス制御リスト (ACL) を使って .asmx ファイルへのアクセスを制限できます。 ただし、WCF の .svc ファイルの Acl は、ASP.NET 互換モードでを除き無視されます。

### <a name="security-role-based-authorization"></a>セキュリティ:ロール ベースの承認

IIS の Windows 認証オプションを、ASP.NET 構成言語の承認要素と組み合わせて使用すると、ASP.NET Web サービスに対し、各ユーザーが属する Windows グループに基づくロール ベースの承認機構を提供できます。 ASP.NET 2.0 には、より汎用的なロール ベースの承認機構である、ロール プロバイダーが導入されました。

ロール プロバイダーとは、ユーザーが割り当てられたロールに関する問い合わせを行う、基本インターフェイスを実装したクラス群です。各ロール プロバイダーには、さまざまな情報源から必要な情報を取得する手段が組み込まれています。 ASP.NET 2.0 には、Microsoft SQL Server データベースからロールの割り当てを検索できるロール プロバイダーと、Windows Server 2003 承認マネージャーから検索できるロール プロバイダーがあります。

ロール プロバイダーのメカニズムは、WCF アプリケーションなど、任意の .NET アプリケーションで ASP.NET とは無関係に実際に使用できます。 WCF アプリケーションの次のサンプルの構成方法を示します、ASP.NET ロール プロバイダーを使用して選択されたオプション、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>します。

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a>セキュリティ:クレーム ベースの承認

WCF の最も重要な技術革新の 1 つは、クレームに基づく保護されたリソースへのアクセスを承認するための完全なサポートです。 クレームは、型、権限、および値で構成されます。たとえば、運転免許証を考えてみましょう。 ここには所持者に関する誕生日などの情報 (ここでいう「クレーム」) が記載されています。 つまり、クレームの型は「誕生日」、値は運転者の実際の誕生日です。 また、クレームの権限は、所持者がこの値に対してできることを表します。 誕生日について言えば、所持者はこの情報を「見る」ことはできますが、「書き換える」ことはできません。 クレーム ベースの承認は、ロール ベースの承認を包含する概念です。というのも、ロールはクレームの 1 つの型であると考えることができるからです。

クレーム ベースの承認では、一連のクレームを操作のアクセス要求と比較し、その結果に応じてアクセスを許可または拒否します。 WCF を使用して値を割り当てることで、クレーム ベースの承認をもう一度実行するクラスを指定することができます、`ServiceAuthorizationManager`プロパティの<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>します。

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

クレーム ベースの承認を行うクラスは、<xref:System.ServiceModel.ServiceAuthorizationManager> を継承し、`AccessCheck()` メソッドだけをオーバーライドして定義します。 WCF サービスの操作が呼び出され、提供されるたびにこのメソッドを呼び出して、 <xref:System.ServiceModel.OperationContext> 、ユーザーのクレームを持つオブジェクトでその`ServiceSecurityContext.AuthorizationContext`プロパティ。 WCF はセキュリティ トークンからユーザーに関するクレームをアセンブル、これが認証に指定されたユーザー、問題の操作をこれらの要求が十分であるかどうかを評価します。

WCF は、任意の種類のセキュリティから要求を自動的に作成トークンは非常に重要な技術革新、認証メカニズムの完全に独立したクレーム ベースの承認のコードを可能になったためです。 これに対し、ACL やロール ベースの承認は、Windows 認証と密に関連し合っています。

### <a name="security-confidentiality"></a>セキュリティ:機密性

ASP.NET Web サービスとの間でやり取りするメッセージの機密性は、トランスポート層で、IIS 上のアプリケーションが Secure Hypertext Transfer Protocol (HTTPS) を使うように構成することによって確保します。 IIS 内でホストされる WCF アプリケーションは、同じを実行できます。 ただし、IIS の外部でホストされる WCF アプリケーションは、セキュリティで保護されたトランスポート プロトコルを使用しても構成できます。 もっと重要な WCF アプリケーションを構成して Ws-security プロトコルを使用して、配送される前に、メッセージをセキュリティで保護することもできます。 メッセージの本体を WS-Security で保護することにより、最終送信先に到達するまでの中継ノードで機密が洩れないようにすることができます。

## <a name="globalization"></a>グローバリゼーション

ASP.NET 構成言語では、個々のサービスごとにカルチャを指定することができます。 WCF では、ASP.NET 互換モードで以外には、その構成設定をサポートしません。 ASP.NET 互換モードを使用しない WCF サービスをローカライズするには、カルチャに固有のアセンブリにサービスの種類をコンパイルして各カルチャに固有のアセンブリのカルチャに固有の別個のエンドポイントがあります。

## <a name="see-also"></a>関連項目

- [使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
