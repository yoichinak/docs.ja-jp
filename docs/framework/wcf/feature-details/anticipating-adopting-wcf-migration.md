---
title: Windows Communication Foundation 導入の準備:将来の移行の簡略化
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 4492626c2cb0958f8aa79fa2b511d9aa9e90b16a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176385"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Windows Communication Foundation 導入の準備:将来の移行の簡略化
新しい ASP.NET アプリケーションの WCF への簡単に将来の移行のために、次の推奨事項と同様に、前の推奨事項に従います。  
  
## <a name="protocols"></a>プロトコル  
 ASP.NET 2.0 の SOAP 1.2 サポートを無効にします。  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>    
      </webServices>  
     </system.web>   
</configuration>  
```  
  
 WCF メッセージは SOAP 1.1 と SOAP 1.2 などのさまざまなプロトコルに準拠している、さまざまなエンドポイントを使用して、移動を必要とするため、これはお勧めします。 サービスが SOAP 1.1 と SOAP 1.2 では、することはできませんが、既定の構成の両方をサポートするために構成されている ASP.NET 2.0 Web 前方参照を確実になる元のアドレスにある単一の WCF エンドポイントに移行する場合はすべて、ASP.NET Web の互換性があります。サービスの既存のクライアント。 また、SOAP 1.1 ではなく 1.2 を選択すると、サービスの利用者がさらに厳しく制限されます。  
  
## <a name="service-development"></a>サービスの開発  
 WCF では、適用することでサービス コントラクトを定義することにより、<xref:System.ServiceModel.ServiceContractAttribute>インターフェイスまたはクラスのいずれか。 この属性は、クラスではなくインターフェイスに適用することをお勧めします。これにより、任意の数のクラスでさまざまに実装できるコントラクト定義が作成されます。 ASP.NET 2.0 では、<xref:System.Web.Services.WebService> 属性をクラスだけでなくインターフェイスに適用することもできます。 ただし、既に説明したように ASP.NET 2.0 には不具合があり、<xref:System.Web.Services.WebService> 属性をクラスではなくインターフェイスに適用した場合、この属性の名前空間パラメーターが有効化されません。 一般に、既定値からのサービスの名前空間を変更することをお勧めであるため`http://tempuri.org`の Namespace パラメーターを使用して、<xref:System.Web.Services.WebService>を適用して ASP.NET Web サービスを定義する 1 つ続行、属性、 <xref:System.ServiceModel.ServiceContractAttribute>インターフェイスまたはクラスのいずれかの属性です。  
  
-   これらのインターフェイスを定義するメソッドに含めるコードは、できるだけ少なくします。 これらのメソッドの作業を他のクラスに委任します。 新しい WCF サービスの種類にし、それらのクラスには、次の実質的な仕事委任も可能性があります。  
  
-   `MessageName` の <xref:System.Web.Services.WebMethodAttribute> パラメーターを使用して、サービスの動作の明示的な名前を指定します。  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     これは、ASP.NET での操作の既定の名前は、WCF によって提供される既定の名前と異なるため、重要です。 明示的な名前を指定することで、既定の名前への依存を避けることができます。  
  
-   WCF がポリモーフィックなメソッドを実装する操作をサポートしていないためを多様メソッドは、ASP.NET Web サービスの操作を実装してください。  
  
-   <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> を使用して、HTTP 要求をメソッドにルーティングする SOAPAction HTTP ヘッダーの明示的な値を指定します。  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     このアプローチには、ASP.NET および WCF が同じで使用する SOAPAction 値を既定値に依存することは回避します。  
  
-   SOAP 拡張機能は使用しないでください。 SOAP 拡張機能が必要な場合、検討している対象の目的は、WCF によって既に提供されている機能であるかどうかを決定します。 そのような場合は実際に場合、WCF を導入しないすぐを再確認します。  
  
## <a name="state-management"></a>状態管理  
 サービスで状態を維持する必要がないようにします。 だけでなく、アプリケーションのスケーラビリティを侵害する傾向がある状態を維持するが、WCF は、ASP.NET 互換モードで ASP.NET のメカニズムをサポートして、ASP.NET および WCF の状態管理メカニズムは非常に異なる。  
  
## <a name="exception-handling"></a>例外処理  
 サービスで送受信するデータ型の構造を設計するときは、クライアントに伝達する必要があり、サービス内で発生する可能性のあるさまざまな種類の例外を表現する構造も設計します。  
  
```csharp  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 これらのクラスには、自分自身を XML にシリアル化する機能を与えます。  
  
```csharp  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 これでこのクラスを使用して、明示的にスローされた <xref:System.Web.Services.Protocols.SoapException> インスタンスの詳細を指定できます。  
  
```csharp  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 これらの例外クラスが、WCF で簡単に再利用が可能<xref:System.ServiceModel.FaultException%601>新しいをスローするクラス `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>セキュリティ  
 セキュリティに関する推奨事項を次にいくつか示します。  
  
-   回避としてそれらを使用して ASP.NET 2.0 のプロファイルを使用して使用が制限 ASP.NET 統合モードの場合は、サービスが WCF に移行されました。  
  
-   インターネット インフォメーション サービス (IIS) を使用して Acl をサポートする ASP.NET Web サービスとしてのサービスへのアクセスを制御する Acl を使用しないように、WCF はありません — をホストするため、ASP.NET Web サービスが IIS に依存し、WCF とは限りませんが、IIS でホストするためです。  
  
-   サービスのリソースへのアクセスを承認するには、ASP.NET 2.0 ロール プロバイダーの使用を検討してください。  
  
## <a name="see-also"></a>関連項目

- [Windows Communication Foundation の採用を予測します。将来的な統合を簡略化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
