---
title: ASP.NET Web サービスとの相互運用
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 41810d8044e4b7ff3193950a914edbf1e61cffb1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464094"
---
# <a name="interoperability-with-aspnet-web-services"></a>ASP.NET Web サービスとの相互運用
ASP.NET Web サービスと Wcf (WCF) Web サービスの間の相互運用性は、両方のテクノロジを使用して実装されたサービスが WS-I 基本プロファイル 1.1 仕様に準拠していることを保証することによって実現できます。 WS-I 基本プロファイル 1.1 に準拠する Web サービスASP.NET、WCF システム提供のバインディング<xref:System.ServiceModel.BasicHttpBinding>を使用して WCF クライアントと相互運用できます。  
  
 属性ASP.NETクラスではなくインターフェイスに<xref:System.Web.Services.WebService>属性と属性<xref:System.Web.Services.WebMethodAttribute>を追加し、次のサンプル コードに示すように、インターフェイスを実装するクラスを記述するオプションを使用します。  
  
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
  
 <xref:System.Web.Services.WebService> 属性を持つインターフェイスは、同じコントラクトを異なる方法で実装する可能性のあるさまざまなクラスで再利用可能なサービスによって実行される操作のコントラクトを構成するため、このオプションを使用することをお勧めします。  
  
 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 属性を使用する場合、`SOAPAction` HTTP ヘッダーではなく、SOAP メッセージの本文要素の完全修飾名に基づいてメッセージをメソッドへルーティングすることは避けます。 WCF は`SOAPAction`、メッセージのルーティングに HTTP ヘッダーを使用します。  
  
 <xref:System.Xml.Serialization.XmlSerializer> によって既定で型のシリアル化が行われる XML は、XML の名前空間が明示的に定義されている場合、<xref:System.Runtime.Serialization.DataContractSerializer> によって型のシリアル化が行われる XML と意味的に同一です。 WCF の採用を見越して ASP.NETWeb サービスで使用するデータ型を定義する場合は、次の操作を行います。  
  
- XML スキーマではなく、.NET Framework クラスを使用して型を定義します。  
  
- <xref:System.SerializableAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> だけをそのクラスに追加します。後者を使用して型の名前空間を明示的に定義してください。 .NET Framework クラスを XML に変換する方法を制御する目的で、<xref:System.Xml.Serialization> 名前空間の属性を追加しないでください。  
  
- この手法を採用すると、後から <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> を追加することで、転送のためにクラスをシリアル化する XML に大きな変更を加えることなく .NET クラスをデータ コントラクトにすることができます。 ASP.NET Web サービスによってメッセージで使用される型は、WCF アプリケーションによってデータ コントラクトとして処理され、WCF アプリケーションのパフォーマンスが向上する他の利点を生み出すことができます。  
  
 インターネット インフォメーション サービス (IIS) に用意されている認証オプションは使用しないでください。 WCF クライアントは、クライアントをサポートしていません。 サービスをセキュリティで保護する必要がある場合は、これらのオプションは堅牢で標準プロトコルに基づいているため、WCF で提供されるオプションを使用します。  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>ServiceModel HttpModule の読み込みがパフォーマンスに及ぼす影響  
 .NET Framework Version 3.0 では、WCF `HttpModule` が、すべての ASP.NET アプリケーションが WCF 対応になるように、ルートの Web.config ファイルにインストールされます。 これによりパフォーマンスに影響が出る場合があるため、次の例に示すように、Web.config ファイルの `ServiceModel` を削除することもできます。  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a>関連項目

- [方法: WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
