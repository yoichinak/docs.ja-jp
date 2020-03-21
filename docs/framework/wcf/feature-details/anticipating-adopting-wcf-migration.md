---
title: 'Windows Communication Foundation の採用: 将来の移行の簡略化'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185471"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Windows Communication Foundation の採用: 将来の移行の簡略化
新しいASP.NET アプリケーションを WCF に移行しやすくするには、前述の推奨事項と次の推奨事項に従います。  
  
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
  
 WCF では、SOAP 1.1 や SOAP 1.2 などの異なるプロトコルに準拠したメッセージを別のエンドポイントを使用して実行する必要があるため、この方法をお勧めします。 ASP.NET 2.0 Web サービスが SOAP 1.1 と SOAP 1.2 の両方をサポートするように構成されている場合 (デフォルトの構成) は、元 ASP.NETのアドレスにある単一の WCF エンドポイントに移行できません。サービスの既存のクライアント。 また、SOAP 1.1 ではなく 1.2 を選択すると、サービスの利用者がさらに厳しく制限されます。  
  
## <a name="service-development"></a>サービスの開発  
 WCF では、インターフェイスまたはクラス<xref:System.ServiceModel.ServiceContractAttribute>のいずれかに適用してサービス コントラクトを定義できます。 この属性は、クラスではなくインターフェイスに適用することをお勧めします。これにより、任意の数のクラスでさまざまに実装できるコントラクト定義が作成されます。 ASP.NET 2.0 では、<xref:System.Web.Services.WebService> 属性をクラスだけでなくインターフェイスに適用することもできます。 ただし、既に説明したように ASP.NET 2.0 には不具合があり、<xref:System.Web.Services.WebService> 属性をクラスではなくインターフェイスに適用した場合、この属性の名前空間パラメーターが有効化されません。 通常は、属性の Namespace パラメーターを使用して、`http://tempuri.org`サービス ASP.NET<xref:System.Web.Services.WebService><xref:System.ServiceModel.ServiceContractAttribute>の名前空間を既定値から変更することをお勧めします。  
  
- これらのインターフェイスを定義するメソッドに含めるコードは、できるだけ少なくします。 これらのメソッドの作業を他のクラスに委任します。 新しい WCF サービスの種類は、これらのクラスにそれらの実質的な作業をデリゲートすることもできます。  
  
- `MessageName` の <xref:System.Web.Services.WebMethodAttribute> パラメーターを使用して、サービスの動作の明示的な名前を指定します。  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     この操作は重要です。なぜなら、ASP.NETの操作の既定の名前は WCF によって提供される既定の名前とは異なるためです。 明示的な名前を指定することで、既定の名前への依存を避けることができます。  
  
- WCF ではポリモーフィック メソッドを使用した操作の実装はサポートされていないため、ポリモーフィック メソッドを使用して ASP.NET Web サービス操作を実装しないでください。  
  
- <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> を使用して、HTTP 要求をメソッドにルーティングする SOAPAction HTTP ヘッダーの明示的な値を指定します。  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     この方法を使用すると、ASP.NETと WCF が同じで使用する既定の SOAPAction 値に依存する必要が回避されます。  
  
- SOAP 拡張機能は使用しないでください。 SOAP 拡張機能が必要な場合は、それらが検討される目的が、既に WCF によって提供されている機能であるかどうかを判断します。 実際にそうである場合は、すぐに WCF を採用しないという選択を再検討してください。  
  
## <a name="state-management"></a>状態管理  
 サービスで状態を維持する必要がないようにします。 状態の維持はアプリケーションのスケーラビリティを損なう傾向があるだけでなく、wcf wcf では互換性モードでASP.NETメカニズムをサポートしていますが、ASP.NETと WCF の状態管理メカニズムは大 ASP.NETきく異なります。  
  
## <a name="exception-handling"></a>例外処理  
 サービスで送受信するデータ型の構造を設計するときは、クライアントに伝達する必要があり、サービス内で発生する可能性のあるさまざまな種類の例外を表現する構造も設計します。  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
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
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 これらの例外クラスは、WCF<xref:System.ServiceModel.FaultException%601>クラスを使用して簡単に再利用可能になり、新しい`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Security  
 セキュリティに関する推奨事項を次にいくつか示します。  
  
- サービスが WCF に移行された場合、ASP.NET統合モードの使用を制限するので、ASP.NET 2.0 プロファイルの使用を避けてください。  
  
- Web サービスがインターネット インフォメーション サービス (IIS) を使用して ACL をサポートASP.NET、WCF ではホスト用の IIS ASP.NET に依存しているため、サービスへのアクセスを制御するために ACL を使用することは避けてください。  
  
- サービスのリソースへのアクセスを承認するには、ASP.NET 2.0 ロール プロバイダーの使用を検討してください。  
  
## <a name="see-also"></a>関連項目

- [Windows Communication Foundation 導入の準備 : 将来的な統合の容易化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
