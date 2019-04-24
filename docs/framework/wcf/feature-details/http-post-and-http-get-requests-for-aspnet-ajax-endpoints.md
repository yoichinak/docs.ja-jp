---
title: '方法: ASP.NET AJAX エンドポイントのために HTTP POST または HTTP GET を選択する'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 33763a77d1ab1c82af9b9e1fb9c42d72392f8798
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091279"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>方法: ASP.NET AJAX エンドポイントのために HTTP POST または HTTP GET を選択する

Windows Communication Foundation (WCF) クライアントの Web サイトの JavaScript から呼び出すことができる ASP.NET AJAX 対応エンドポイントを公開するサービスを作成することができます。 このようなサービスを構築するための基本的な手順については説明[方法。ASP.NET AJAX エンドポイントを追加する構成を使用して](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)と[方法。構成を使用せずに ASP.NET AJAX エンドポイントを追加](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)します。  
  
 ASP.NET AJAX では、HTTP POST 動詞および HTTP GET 動詞を使用する操作をサポートしており、HTTP POST が既定となっています。 副作用がなく、返されるデータがほとんど、またはまったく変更されない操作を作成する場合は、代わりに HTTP GET を使用します。 GET 操作の結果はキャッシュされます。つまり、同じ操作についての複数の呼び出し結果がサービスに対する 1 回だけの要求で済むことになります。 WCF では行われませんが、任意のレベル (ユーザーのブラウザーでプロキシ サーバーでは、その他のレベルです。) を実行できる、キャッシュキャッシュはサービス パフォーマンスの向上が望まれる場合には有効ですが、データの変更が頻繁であったり、操作によって何かのアクションが実行される場合は適していません。  
  
 たとえば、ユーザーの音楽ライブラリを管理するサービスをデザインする場合、アルバムのタイトルに基づいてアーティストを検索する操作では GET の使用は役に立ちますが、ユーザーの個人コレクションにアルバムを追加する操作では POST を使用する必要があります。  
  
 キャッシュの有効期間を制御するには、<xref:System.ServiceModel.Web.OutgoingWebResponseContext> 型を使用します。 たとえば、1 時間ごとに更新される天気予報を返すサービスをデザインする場合、GET を使用することが考えられますが、サービスを使用するユーザーが古いデータにアクセスすることを防止するために、キャッシュの有効期間を 1 時間以内に制限します。  
  
 Script Manager コントロールを使用する ASP.NET AJAX ページからサービスを使用する場合は、Script Manager のメカニズムにより適切な要求の種類が発行されることが保証されているため、操作で GET と POST のどちらを使用しても違いはありません。  
  
 HTTP GET 操作では、複合型データ コントラクト型も含めて、POST 操作でサポートされるすべての入力パラメーターを使用できます。 ただし、多くの場合、キャッシュの効率が低下するため、多数のパラメーター、または複雑すぎるパラメーターを GET 操作で使用しないことをお勧めします。  
  
 このトピックでは、<xref:System.ServiceModel.Web.WebGetAttribute> または <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性を追加することで、サービス コントラクトに適切な操作を GET と POST から選択する方法について説明します。 実行中のサービスを取得するために必要なその他の手順 (構成の実装、およびサービスをホスト) には、WCF、ASP.NET AJAX サービスで使用されるものと似ています。  
  
 <xref:System.ServiceModel.Web.WebGetAttribute> でマークされた操作では、常に GET 要求が使用されます。 <xref:System.ServiceModel.Web.WebInvokeAttribute> でマークされた操作と、これらの 2 つの属性のどちらでもマークされていない操作では、POST 要求が使用されます。 <xref:System.ServiceModel.Web.WebInvokeAttribute> は、<xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> プロパティを介して、GET と POST 以外の HTTP 動詞 (PUT や DELETE など) の使用を許可します。 ただし、これらの動詞は ASP.NET AJAX ではサポートされていません。 Script Manager コントロールを使用して ASP.NET ページからサービスを使用する場合は、<xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> プロパティは使用しないでください。  
  
 GET に切り替えるの実際の例を参照してください、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプル。  
  
 POST を使用するサンプルを参照してください、 [AJAX サービスを使用して HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)サンプル。  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>HTTP GET または HTTP POST 要求に応答する WCF サービスを作成するには
  
1. マークされたインターフェイスでの基本的な WCF サービス コントラクトの定義、<xref:System.ServiceModel.ServiceContractAttribute>属性。 各操作を <xref:System.ServiceModel.OperationContractAttribute> でマークします。 <xref:System.ServiceModel.Web.WebGetAttribute> 属性を追加して、操作が HTTP GET 要求に応答するように指定します。 HTTP POST を明示的に指定するために <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性を追加することもできます。また、属性を指定しなければ、既定で HTTP POST となります。
  
    ```csharp
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. `IMusicService` を使用して、`MusicService` サービス コントラクトを実装します。
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. アプリケーションで、.svc という拡張子を付けて新しい service ファイルを作成します。 このファイルを追加、適切な編集[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブ情報をサービスします。 指定、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>で使用される、 [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブを自動的に ASP.NET AJAX エンドポイントを構成します。  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>サービスを呼び出すには  
  
1. ブラウザーを使用すると、クライアントのコードなしでサービスの GET 操作をテストできます。 サービスが構成されている場合など、 `http://example.com/service.svc` 」と入力し、アドレス`http://example.com/service.svc/LookUpArtist?album=SomeAlbum`アドレス バーには、ブラウザーにサービスを呼び出すし、応答をダウンロードまたは表示します。
  
2. GET 操作によるサービスは、他の ASP.NET AJAX サービスと同様に、サービス URL を ASP.NET AJAX Script Manager コントロールのスクリプト コレクションに入力することで使用できます。 例については、次を参照してください。、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)します。
  
## <a name="see-also"></a>関連項目

- [ASP.NET AJAX 用の WCF サービスの作成](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [方法: AJAX 対応 ASP.NET Web サービスを WCF に移行します。](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
