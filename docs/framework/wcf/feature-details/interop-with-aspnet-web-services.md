---
title: ASP.NET Web サービスとの相互運用
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: f2f1a8fd2bf34ff61784f2dcb88c0669585da573
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026025"
---
# <a name="interoperability-with-aspnet-web-services"></a>ASP.NET Web サービスとの相互運用
両方のテクノロジを使用して実装されているサービスが、WS に準拠していることを確認して、ASP.NET Web サービスと Windows Communication Foundation (WCF) Web サービスの間の相互運用性を実現できます-Basic Profile 1.1 仕様。 WS に準拠する ASP.NET Web サービスの基本プロファイル 1.1 は WCF のシステム指定のバインディングを使用して WCF クライアントと相互運用可能<xref:System.ServiceModel.BasicHttpBinding>します。  
  
 ASP.NET 2.0 を追加するオプションを使用して、<xref:System.Web.Services.WebService>と<xref:System.Web.Services.WebMethodAttribute>属性クラスの場合、次のサンプル コードに示すように、インターフェイスを実装するクラスを記述してではなくインターフェイスです。  
  
```  
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
  
 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 属性を使用する場合、`SOAPAction` HTTP ヘッダーではなく、SOAP メッセージの本文要素の完全修飾名に基づいてメッセージをメソッドへルーティングすることは避けます。 WCF を使用して、`SOAPAction`メッセージのルーティング用の HTTP ヘッダー。  
  
 <xref:System.Xml.Serialization.XmlSerializer> によって既定で型のシリアル化が行われる XML は、XML の名前空間が明示的に定義されている場合、<xref:System.Runtime.Serialization.DataContractSerializer> によって型のシリアル化が行われる XML と意味的に同一です。 を導入する WCF に応じるためにそのサービスで使用するためのデータ型を定義するときは、次の操作を行います。  
  
- XML スキーマではなく、.NET Framework クラスを使用して型を定義します。  
  
- <xref:System.SerializableAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> だけをそのクラスに追加します。後者を使用して型の名前空間を明示的に定義してください。 .NET Framework クラスを XML に変換する方法を制御する目的で、<xref:System.Xml.Serialization> 名前空間の属性を追加しないでください。  
  
- この手法を採用すると、後から <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> を追加することで、転送のためにクラスをシリアル化する XML に大きな変更を加えることなく .NET クラスをデータ コントラクトにすることができます。 ASP.NET Web サービスでのメッセージで使用される型として処理できますデータ コントラクト、WCF アプリケーションで、特に他の特典では、WCF アプリケーションでパフォーマンスが向上します。  
  
 インターネット インフォメーション サービス (IIS) に用意されている認証オプションは使用しないでください。 WCF クライアントでは、そのサポートしていません。 サービスをセキュリティで保護する必要があります、これらのオプションは、堅牢な標準プロトコルに基づいているために、WCF によって提供されるオプションを使用します。  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>ServiceModel HttpModule の読み込みがパフォーマンスに及ぼす影響  
 .NET Framework Version 3.0 では、WCF `HttpModule` が、すべての ASP.NET アプリケーションが WCF 対応になるように、ルートの Web.config ファイルにインストールされます。 これによりパフォーマンスに影響が出る場合があるため、次の例に示すように、Web.config ファイルの `ServiceModel` を削除することもできます。  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>関連項目

- [方法: ASP.NET Web サービス クライアントと相互運用する WCF サービスを構成します。](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
