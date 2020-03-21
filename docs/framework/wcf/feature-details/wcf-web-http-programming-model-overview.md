---
title: WCF Web HTTP プログラミング モデルの概要
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: fb6ef0fdcefbc6ceec75ce30db3abf5896d85c61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184185"
---
# <a name="wcf-web-http-programming-model-overview"></a>WCF Web HTTP プログラミング モデルの概要
WCF (WCF) WEB HTTP プログラミング モデルは、WCF を使用して WEB HTTP サービスを構築するために必要な基本的な要素を提供します。 WCF WEB HTTP サービスは、Web ブラウザーを含む、可能なクライアントの範囲が最も広い範囲でアクセスするように設計されており、次の固有の要件があります。  
  
- **URI と URI 処理**URI は、WEB HTTP サービスの設計において中心的な役割を果たします。 WCF WEB HTTP プログラミング モデル<xref:System.UriTemplate>では<xref:System.UriTemplateTable>、 および クラスを使用して URI 処理機能を提供します。  
  
- **GET および POST 操作のサポート**WEB HTTP サービスは、データの変更やリモート呼び出しに対するさまざまな呼び出しに加えて、GET 動詞を使用してデータを取得します。 WCF WEB HTTP プログラミング モデル<xref:System.ServiceModel.Web.WebGetAttribute>では<xref:System.ServiceModel.Web.WebInvokeAttribute>、 と を使用して、GET と、PUT、POST、および DELETE などの他の HTTP 動詞の両方にサービス操作を関連付けます。  
  
- **複数のデータ形式**Web スタイルのサービスは、SOAP メッセージに加えて、多くの種類のデータを処理します。 WCF WEB HTTP プログラミング モデル<xref:System.ServiceModel.WebHttpBinding>では<xref:System.ServiceModel.Description.WebHttpBehavior>、 XML ドキュメント、JSON データ オブジェクト、およびバイナリ コンテンツのストリーム (イメージ、ビデオ ファイル、プレーン テキストなど) など、さまざまなデータ形式を使用して、  
  
 WCF WEB HTTP プログラミング モデルは、WEB HTTP サービス、AJAX および JSON サービス、およびシンジケーション (ATOM/RSS) フィードを含む Web スタイルのシナリオをカバーする WCF の範囲を拡張します。 AJAX および JSON サービスの詳細については、「 [AJAX 統合と JSON サポート](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)」を参照してください。 配信の詳細については、「 WCF 配信の[概要](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)」を参照してください。  
  
 WEB HTTP サービスから返されるデータの種類に追加の制限はありません。 WEB HTTP サービス操作からは任意のシリアル化可能な型を返すことができます。 WEB HTTP サービス操作は Web ブラウザーによって呼び出すことができるため、URL に指定できるデータ型に制限があります。 既定でサポートされる型の詳細については、以下の **「UriTemplate クエリ文字列パラメーターと URL」セクションを**参照してください。 既定の動作は、URL で指定されたパラメーターから実際のパラメーター型への変換方法を指定する独自の T:System.ServiceModel.Dispatcher.QueryStringConverter 実装を提供することで変更できます。 詳細については、<xref:System.ServiceModel.Dispatcher.QueryStringConverter> を参照してください。  
  
> [!CAUTION]
> WCF WEB HTTP プログラミング モデルで作成されたサービスは、SOAP メッセージを使用しません。 SOAP は使用されないため、WCF によって提供されるセキュリティ機能は使用できません。 ただし、HTTPS でサービスをホストすることによってトランスポート ベースのセキュリティを使用できます。 WCF セキュリティの詳細については、「セキュリティの[概要](../../../../docs/framework/wcf/feature-details/security-overview.md)」を参照してください。  
  
> [!WARNING]
> IIS の WebDAV 拡張をインストールすると、WebDAV 拡張がすべての PUT 要求を処理しようとしたときに Web HTTP サービスが HTTP 405 エラーを返すことがあります。 この問題を解決するには、WebDAV 拡張をアンインストールするか、Web サイトの WebDAV 拡張を無効にします。 詳細については[、IIS および WebDav を参照してください。](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>UriTemplate および UriTemplateTable を使用した URI 処理  
 URI テンプレートには、構造的に類似する URI の大規模なセットを効率的に表現するための構文が備わっています。 たとえば、テンプレート a/{segment}/c は、中間のセグメントの値を問わず、"a" で始まり "c" で終了する 3 つのセグメントから成る URI のセットを表しています。  
  
 このテンプレートによって、次のような URI が記述されます。  
  
- a/x/c  
  
- a/y/c  
  
- a/z/c  
  
- その他にもあります。  
  
 このテンプレートでは、中かっこによる表記 ("{segment}") で、リテラル値ではなく、変数のセグメントを示しています。  
  
 .NET Framework は <xref:System.UriTemplate> という URI テンプレートでの作業に使用できる新しい API を提供します。 `UriTemplates` を使用すると、次のことができます。  
  
- パラメーターのセットを使用して`Bind`メソッドの 1 つを呼び出して、テンプレートに一致する*完全閉じた URI*を生成できます。 つまり、URI テンプレート内の変数がすべて、実際の値に置き換えられます。  
  
- 候補の URI を使用して `Match`() を呼び出すことができます。このメソッドは、テンプレートを使用して候補の URI を構成要素に分解し、テンプレート内の変数に従って分類される URI のさまざまな要素を収めたディクショナリを返します。  
  
- `Bind`() と `Match`() は逆のもので、`Match`( `Bind`( x ) ) を呼び出し、最初と同じ環境に戻ることができます。  
  
 包含されたテンプレートを個別に扱うことができるデータ構造内の一連の <xref:System.UriTemplate> オブジェクトを追跡することが必要になる場合がよくあります (特に、URI に基づいて要求をサービス操作にディスパッチすることが必要なサーバー上)。 <xref:System.UriTemplateTable> は、URI テンプレートのセットを表し、テンプレート セットと候補の URI が与えられると、最適の組み合わせを選択します。 これは特定のネットワーク スタック (WCF を含む) とは関係ないので、必要に応じて使用できます。  
  
 WCF サービス モデルは、<xref:System.UriTemplate> および <xref:System.UriTemplateTable> を使用して、<xref:System.UriTemplate> によって記述された URI セットにサービス操作を関連付けます。 サービス操作は、<xref:System.UriTemplate> または <xref:System.ServiceModel.Web.WebGetAttribute> によって <xref:System.ServiceModel.Web.WebInvokeAttribute> に関連付けられます。 および の<xref:System.UriTemplateTable>詳細<xref:System.UriTemplate>については[、「Uri テンプレートと Uri テンプレート テーブル」を参照してください。](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet および WebInvoke 属性  
 WCF WEB HTTP サービスでは、さまざまな呼び出しの動詞 (HTTP POST、PUT、および DELETE など) に加えて、取得動詞 (HTTP GET など) を使用します。 WCF WEB HTTP プログラミング モデルを使用すると、サービス開発者は、<xref:System.ServiceModel.Web.WebGetAttribute>と とのサービス操作に関連付<xref:System.ServiceModel.Web.WebInvokeAttribute>けられている URI テンプレートと動詞の両方を制御できます。 <xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> を使用すると、個々の操作を URI と、それらの URI に関連付けられている HTTP メソッドにバインドする方法を制御できます。 たとえば、次のコードでは、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> を追加します。  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,
                               string newName );  
}  
```  
  
 上記のコードを使用すると、次の HTTP 要求を行うことができます。  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> は、既定で POST に設定されていますが、他の動詞にも使用できます。  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 WCF WEB HTTP プログラミング モデルを使用する WCF サービスの完全なサンプルを参照してください[方法: 基本的な WCF Web HTTP サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>UriTemplate クエリ文字列パラメーターと URL  
 サービス操作に関連付けられた URL を入力することによって、Web ブラウザーから Web スタイルのサービスを呼び出すことができます。 このようなサービス操作は、文字列形式で指定する必要があるクエリ文字列パラメーターを URL 内で受け取ることができます。 次の表に、URL 内で渡すことができる型と、使用される形式を示します。  
  
|Type|Format|  
|----------|------------|  
|<xref:System.Byte>|0 から 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (指数表記は要求されない)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (指数表記は要求されない)|  
|<xref:System.Char>|任意の 1 文字|  
|<xref:System.Decimal>|標準表記による任意の小数 (指数なし)|  
|<xref:System.Boolean>|True または False (大文字と小文字は区別されません)|  
|<xref:System.String>|任意の文字列 (null 文字列はサポートされず、エスケープは行われない)|  
|<xref:System.DateTime>|MM/DD/YYYY<br /><br /> MM/DD/YYYY HH:MM:SS [午前&#124;PM]<br /><br /> 月 日 年<br /><br /> 月日年 HH:MM:SS [午前&#124;時]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> DD = 日、HH = 時、MM = 分、SS = 秒|  
|<xref:System.Guid>|GUID。たとえば、次のようになります。<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/YYYY HH:MM:SS MM:SS<br /><br /> DD = 日、HH = 時、MM = 分、SS = 秒|  
|列挙型|列挙値。たとえば、次のコードのように列挙体を定義します。<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> クエリ文字列に、任意の列挙値 (またはそれぞれに対応する integer 値) を指定できます。|  
|型と文字列表現を双方向に変換できる `TypeConverterAttribute` を持つ型。|型コンバーターによって異なります。|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>形式と WCF WEB HTTP プログラミング モデル  
 WCF WEB HTTP プログラミング モデルには、さまざまなデータ形式で動作する新機能があります。 <xref:System.ServiceModel.WebHttpBinding> は、バインディング層で次のさまざまな種類のデータを読み書きできます。  
  
- XML  
  
- JSON  
  
- 不透明なバイナリ ストリーム  
  
 つまり、WCF WEB HTTP プログラミング モデルは任意の種類のデータを処理できますが、プログラミングを<xref:System.IO.Stream>行う場合があります。  
  
 .NET Framework 3.5 では、JSON データ (AJAX) とシンジケーション フィード (ATOM および RSS を含む) のサポートが提供されます。 これらの機能の詳細については、「 [WCF Web HTTP の書式設定](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)WCF[配信の概要](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)」および[「AJAX 統合と JSON サポート](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)」を参照してください。  
  
## <a name="wcf-web-http-programming-model-and-security"></a>WCF WEB HTTP プログラミング モデルとセキュリティ  

WCF WEB HTTP プログラミング モデルは WS-* プロトコルをサポートしていないため、WCF WEB HTTP サービスをセキュリティで保護する唯一の方法は、SSL を使用して HTTPS 経由でサービスを公開することです。 IIS 7.0 で SSL をセットアップする方法の詳細については、「 [IIS で SSL を実装する方法](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis)」を参照してください。
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>WCF WEB HTTP プログラミング モデルのトラブルシューティング  
 <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> を使用してチャネルを作成するために WCF WEB HTTP サービスを呼び出すと、異なる <xref:System.ServiceModel.Description.WebHttpBehavior> が <xref:System.ServiceModel.EndpointAddress> に渡されるとしても、<xref:System.ServiceModel.EndpointAddress> は構成ファイルに設定されている <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> を使用します。  
  
## <a name="see-also"></a>関連項目

- [WCF 配信](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [WCF Web HTTP プログラミング オブジェクト モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
