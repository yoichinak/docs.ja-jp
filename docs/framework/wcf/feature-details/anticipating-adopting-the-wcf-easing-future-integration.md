---
title: Windows Communication Foundation 導入の準備:将来的な統合の容易化
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 2f733f9cc33846913539fee4afdd95efa9224058
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124801"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Windows Communication Foundation 導入の準備:将来的な統合の容易化
現在 ASP.NET を使用して WCF を今後の使用が予想される場合、このトピックは、WCF アプリケーションと共に、新しい ASP.NET Web サービスが動作することを確認するためのガイダンスを示します。  
  
## <a name="general-recommendations"></a>一般的な推奨事項  
 ASP.NET 2.0 を使用して、すべての新規サービスを作成します。 こうすることで、拡張および強化された新バージョンの機能にアクセスできます。 ただし、その方法は、同じアプリケーションで WCF コンポーネントと共に ASP.NET 2.0 コンポーネントを使用する可能性のもできます。  
  
## <a name="protocols"></a>プロトコル  
 WS-I Basic Profile 1.1 への準拠を検証するには、次のように ASP.NET 2.0 の新機能を使用します。  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 WS に準拠する ASP.NET Web サービスのバインド、定義済みの WCF を使用して WCF クライアントと相互運用可能な基本プロファイル 1.1 なります<xref:System.ServiceModel.BasicHttpBinding>します。  
  
## <a name="service-development"></a>サービスの開発  
 SOAPAction HTTP ヘッダーではなく、SOAP メッセージの本文要素の完全修飾名に基づいてメッセージをメソッドにルーティングする場合は、<xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 属性の使用を避けます。 WCF は、SOAPAction HTTP ヘッダーを使用してメッセージをルーティングします。  
  
## <a name="data-representation"></a>データ表現  
 <xref:System.Xml.Serialization.XmlSerializer> によって既定で型のシリアル化が行われる XML は、XML の名前空間が明示的に定義されている場合、<xref:System.Runtime.Serialization.DataContractSerializer> によって型のシリアル化が行われる XML と意味的に同一です。 を導入する WCF を見越して、今後の ASP.NET Web サービスで使用するためのデータ型を定義するときは、次の操作を行います。  
  
1.  XML スキーマではなく、.NET Framework クラスを使用して型を定義します。  
  
2.  <xref:System.SerializableAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> だけをそのクラスに追加します。後者を使用して型の名前空間を明示的に定義してください。 .NET Framework クラスを XML に変換する方法を制御する目的で、<xref:System.Xml.Serialization> 名前空間の属性を追加しないでください。  
  
 この手法を採用すると、後から <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> を追加することで、転送のためにクラスをシリアル化する XML に大きな変更を加えることなく .NET クラスをデータ コントラクトにすることができます。 ASP.NET Web サービスでのメッセージで使用される型できるようになります、WCF アプリケーションでデータ コントラクトとして処理するその他の特典では、WCF アプリケーションのパフォーマンス向上の間で、生成します。  
  
## <a name="security"></a>セキュリティ  
 インターネット インフォメーション サービス (IIS) に用意されている認証オプションは使用しないでください。 WCF クライアントでは、そのサポートしていません。 保護されるように、サービスに必要な場合は、これらのオプションの幅が広く、標準のプロトコルに基づいているため、WCF が提供するオプションを使用します。  
  
## <a name="see-also"></a>関連項目

- [Windows Communication Foundation 導入の準備:将来の移行の簡略化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
