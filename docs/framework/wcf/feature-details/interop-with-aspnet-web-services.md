---
title: ASP.NET Web サービスとの相互運用
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 16e22a091b88d12abccb063d2407db82460458c6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638607"
---
# <a name="interoperability-with-aspnet-web-services"></a>ASP.NET Web サービスとの相互運用
間の相互運用[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]WS に両方のテクノロジを使用して実装されているサービスが準拠していることを確認して Web サービスと Windows Communication Foundation (WCF) Web サービスを実現できます-Basic Profile 1.1 仕様。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] WS に準拠している web サービスの基本プロファイル 1.1 は WCF のシステム指定のバインディングを使用して WCF クライアントと相互運用可能<xref:System.ServiceModel.BasicHttpBinding>します。  
  
 次のサンプル コードに示すように、[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 属性と <xref:System.Web.Services.WebService> 属性をインターフェイス (クラスではありません) に追加し、そのインターフェイスを実装するクラスを作成するという、<xref:System.Web.Services.WebMethodAttribute> のオプションを使用します。  
  
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
  
 <xref:System.Xml.Serialization.XmlSerializer> によって既定で型のシリアル化が行われる XML は、XML の名前空間が明示的に定義されている場合、<xref:System.Runtime.Serialization.DataContractSerializer> によって型のシリアル化が行われる XML と意味的に同一です。 使用するためのデータ型を定義するときに[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web で WCF を採用する予定のサービスで、次の操作を行います。  
  
- XML スキーマではなく、.NET Framework クラスを使用して型を定義します。  
  
- <xref:System.SerializableAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> だけをそのクラスに追加します。後者を使用して型の名前空間を明示的に定義してください。 .NET Framework クラスを XML に変換する方法を制御する目的で、<xref:System.Xml.Serialization> 名前空間の属性を追加しないでください。  
  
- この手法を採用すると、後から <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> を追加することで、転送のためにクラスをシリアル化する XML に大きな変更を加えることなく .NET クラスをデータ コントラクトにすることができます。 メッセージ内で使用される型[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web サービスは、WCF アプリケーションでパフォーマンスの向上を特にメリットが、応答して、WCF アプリケーションでデータ コントラクトとして処理できます。  
  
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
