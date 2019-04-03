---
title: クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: ff68a8bee17b55f7865d6f6c289ba514729be70d
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093446"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)
公開するサービスにアクセスすることができます、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードで Web ブラウザーに URI を指定します。 URI はリソースのアドレスを提供し、要求メッセージがこれらのアドレスに送信されてリソースが表す基になるデータのアクセスまたは変更を行います。 ブラウザーは HTTP GET コマンドを発行して、要求されたリソースを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして返します。 詳細については、[Web ブラウザーからサービスへのアクセス](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)を参照してください。  
  
 Web ブラウザーは [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスが予期されたデータを返すかどうかをテストするために便利ですが、データの作成、更新、および削除も行うことができる運用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスは、一般的にアプリケーション コードや Web ページのスクリプト言語を使用してアクセスします。 このトピックにアクセスする方法の概要を示します[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]クライアント アプリケーションからのフィードします。  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>REST セマンティクスを使用したデータのアクセスおよび変更  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 公開するサービス間の相互運用性を保証するのに役立ちます[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードと使用するアプリケーション[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。 アプリケーション アクセスし、データの変更、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-ベースのサービスを特定の HTTP アクションのおよび URI、アクションの対象となるエンティティ リソースのアドレスを要求メッセージを送信します。 エンティティ データを指定する必要がある場合、メッセージの本文に、エンコードされたペイロードとして明示的に指定します。  
  
### <a name="http-actions"></a>HTTP アクション  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、アドレス指定されたリソースが表すエンティティ データに対する操作の作成、読み取り、更新、および削除を実行する次の HTTP アクションをサポートします。  
  
-   **HTTP GET** -これは、ブラウザーからリソースにアクセスする場合の既定のアクション。 要求メッセージではペイロードは指定されず、要求されたデータを含むペイロードを含む応答メソッドが返されます。  
  
-   **HTTP POST** -指定されたリソースに新しいエンティティ データを挿入します。 挿入するデータは、要求メッセージのペイロードで指定されます。 応答メッセージのペイロードには、新しく作成されたエンティティのデータが含まれます。 これには自動生成されたキー値が含まれます。 ヘッダーには、新しいエンティティ リソースのアドレスを指定する URI も含まれます。  
  
-   **HTTP DELETE** -指定されたリソースが表すエンティティ データを削除します。 ペイロードは要求メッセージおよび応答メッセージ内に存在しません。  
  
-   **HTTP PUT** - 既存のエンティティ データを要求されたリソースを要求メッセージのペイロードで指定されている新しいデータで置き換えます。  
  
-   **HTTP MERGE** - をエンティティのデータを変更するだけのデータ ソースで挿入、削除を実行する非効率[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]新しい HTTP MERGE アクションが導入されています。 要求メッセージのペイロードには、アドレス指定されたエンティティ リソースで変更する必要のあるプロパティが含まれます。 HTTP MERGE は HTTP 仕様で定義されていないので、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 対応のサーバー以外で HTTP MERGE 要求をルーティングするには追加の処理が必要になる場合があります。  
  
 詳細については、次を参照してください[OData:。操作](https://go.microsoft.com/fwlink/?LinkId=185792)します。  
  
### <a name="payload-formats"></a>ペイロード形式  
 HTTP PUT、HTTP POST、または HTTP MERGE 要求の場合、要求メッセージのペイロードは、データ サービスに送信するエンティティ データを含んでいます。 ペイロードのコンテンツは、メッセージのデータ形式によって異なります。 そのようなペイロードは、DELETE 以外のすべてのアクションに対する HTTP 応答にも含まれます。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] アクセスして、サービスでのデータを変更するのには、次のペイロード形式をサポートしています。  
  
-   **Atom** -によって定義されている XML ベースのメッセージ エンコーディング[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Atom Publishing Protocol (AtomPub) の Web フィード、ポッド キャスト、wiki、HTTP 経由のデータ交換を有効にして XML ベースのインターネット機能の拡張機能として。 詳細については、次を参照してください[OData:。Atom 形式](https://go.microsoft.com/fwlink/?LinkId=185794)します。  
  
-   **JSON** -JavaScript Object Notation (JSON) は、JavaScript プログラミング言語のサブセットに基づく軽量データ交換形式。 詳細については、次を参照してください[OData:。JSON 形式](https://go.microsoft.com/fwlink/?LinkId=185795)します。  
  
 ペイロードのメッセージ形式は、HTTP 要求メッセージのヘッダーで要求されます。 詳細については、次を参照してください[OData:。操作](https://go.microsoft.com/fwlink/?LinkID=185792)します。  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>クライアント ライブラリを使用したデータのアクセスおよび変更  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 簡単に使用できるようにするクライアント ライブラリが含まれています、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .NET Framework および Silverlight ベースのクライアント アプリケーションからフィードします。 これらのライブラリは、HTTP メッセージの送受信を簡略化します。 また、メッセージ ペイロードをエンティティ データを表す CLR オブジェクトに変換します。 クライアント ライブラリには、 <xref:System.Data.Services.Client.DataServiceContext> および <xref:System.Data.Services.Client.DataServiceQuery%601>という 2 つのコア クラスがあります。 これらのクラスを使用すると、データ サービスをクエリして、返されるエンティティ データを CLR オブジェクトとして処理できます。 詳細については、[WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)と[WCF Data Services (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))を参照してください。  
  
 使用することができます、**サービス参照の追加**データ サービスへの参照を追加する Visual Studio でダイアログ。 このツールは、参照されたデータ サービスからサービス メタデータを要求し、データ サービスを表す <xref:System.Data.Services.Client.DataServiceContext> を生成します。また、エンティティを表すクライアント データ サービス クラスも生成します。 詳細については、[データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)を参照してください。  
  
 プログラミング ライブラリを使用するように使用できますが、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]その他のクライアント アプリケーションにフィードします。 詳細については、、 [OData SDK](https://go.microsoft.com/fwlink/?LinkId=185796)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [データ サービス リソースへのアクセス](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
- [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
