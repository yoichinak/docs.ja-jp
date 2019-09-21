---
title: クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 050c1a67a367a6dd5175c535fe89fb0010ae8cbc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790281"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)
Web ブラウザーに URI を指定すること[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]によって、フィードを公開するサービスにアクセスできます。 URI はリソースのアドレスを提供し、要求メッセージがこれらのアドレスに送信されてリソースが表す基になるデータのアクセスまたは変更を行います。 ブラウザーは HTTP GET コマンドを発行して、要求されたリソースを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして返します。 詳細については、「 [Web ブラウザーからサービスにアクセス](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)する」を参照してください。  
  
 Web ブラウザーは [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスが予期されたデータを返すかどうかをテストするために便利ですが、データの作成、更新、および削除も行うことができる運用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスは、一般的にアプリケーション コードや Web ページのスクリプト言語を使用してアクセスします。 このトピックでは、クライアントアプリケーションからフィード[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]にアクセスする方法の概要について説明します。  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>REST セマンティクスを使用したデータのアクセスおよび変更  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]は、フィードを公開[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]するサービスと、フィードを使用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]するアプリケーションの間の相互運用性を保証するのに役立ちます。 アプリケーションは、特定の HTTP アクション[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]の要求メッセージと、アクションを実行するエンティティリソースをアドレス指定する URI を送信することによって、ベースのサービス内のデータにアクセスして変更します。 エンティティ データを指定する必要がある場合、メッセージの本文に、エンコードされたペイロードとして明示的に指定します。  
  
### <a name="http-actions"></a>HTTP アクション  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、アドレス指定されたリソースが表すエンティティ データに対する操作の作成、読み取り、更新、および削除を実行する次の HTTP アクションをサポートします。  
  
- **HTTP GET** -これは、ブラウザーからリソースにアクセスするときの既定のアクションです。 要求メッセージではペイロードは指定されず、要求されたデータを含むペイロードを含む応答メソッドが返されます。  
  
- **HTTP POST** -指定されたリソースに新しいエンティティデータを挿入します。 挿入するデータは、要求メッセージのペイロードで指定されます。 応答メッセージのペイロードには、新しく作成されたエンティティのデータが含まれます。 これには自動生成されたキー値が含まれます。 ヘッダーには、新しいエンティティ リソースのアドレスを指定する URI も含まれます。  
  
- **HTTP DELETE** -指定されたリソースが表すエンティティデータを削除します。 ペイロードは要求メッセージおよび応答メッセージ内に存在しません。  
  
- **HTTP PUT** -要求されたリソースの既存のエンティティデータを、要求メッセージのペイロードで指定された新しいデータで置き換えます。  
  
- **HTTP マージ**-エンティティデータを変更するためだけに削除を実行した後、データソースに挿入を実行[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]すると、によって、新しい http マージアクションが導入されます。 要求メッセージのペイロードには、アドレス指定されたエンティティ リソースで変更する必要のあるプロパティが含まれます。 HTTP MERGE は HTTP 仕様で定義されていないので、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 対応のサーバー以外で HTTP MERGE 要求をルーティングするには追加の処理が必要になる場合があります。  
  
 詳細については[、「OData:操作](https://go.microsoft.com/fwlink/?LinkId=185792)。  
  
### <a name="payload-formats"></a>ペイロード形式  
 HTTP PUT、HTTP POST、または HTTP MERGE 要求の場合、要求メッセージのペイロードは、データ サービスに送信するエンティティ データを含んでいます。 ペイロードのコンテンツは、メッセージのデータ形式によって異なります。 そのようなペイロードは、DELETE 以外のすべてのアクションに対する HTTP 応答にも含まれます。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]では、サービスを使用してデータにアクセスして変更するための次のペイロード形式がサポートされています。  
  
- **Atom** -Web フィード、ポッドキャスト、wiki、および XML ベース[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]のインターネット機能に対して HTTP 経由のデータ交換を有効にするために、によって atom Publishing Protocol (AtomPub) の拡張機能として定義される xml ベースのメッセージエンコーディング。 詳細については[、「OData:Atom 形式](https://go.microsoft.com/fwlink/?LinkId=185794)。  
  
- **Json (json** ) は、JavaScript プログラミング言語のサブセットに基づく軽量のデータ交換形式で、json (json) JavaScript Object Notation ます。 詳細については[、「OData:JSON 形式](https://go.microsoft.com/fwlink/?LinkId=185795)。  
  
 ペイロードのメッセージ形式は、HTTP 要求メッセージのヘッダーで要求されます。 詳細については[、「OData:操作](https://go.microsoft.com/fwlink/?LinkID=185792)。  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>クライアント ライブラリを使用したデータのアクセスおよび変更  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]には、.NET Framework および Silverlight ベースのクライアントアプリケーションから[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードを簡単に使用できるようにするクライアントライブラリが含まれています。 これらのライブラリは、HTTP メッセージの送受信を簡略化します。 また、メッセージ ペイロードをエンティティ データを表す CLR オブジェクトに変換します。 クライアント ライブラリには、 <xref:System.Data.Services.Client.DataServiceContext> および <xref:System.Data.Services.Client.DataServiceQuery%601>という 2 つのコア クラスがあります。 これらのクラスを使用すると、データ サービスをクエリして、返されるエンティティ データを CLR オブジェクトとして処理できます。 詳細については、「 [WCF Data Services クライアントライブラリ](wcf-data-services-client-library.md)と[WCF Data Services (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))」を参照してください。  
  
 Visual Studio の **[サービス参照の追加]** ダイアログボックスを使用して、データサービスへの参照を追加できます。 このツールは、参照されたデータ サービスからサービス メタデータを要求し、データ サービスを表す <xref:System.Data.Services.Client.DataServiceContext> を生成します。また、エンティティを表すクライアント データ サービス クラスも生成します。 詳細については、「[データサービスクライアントライブラリの生成](generating-the-data-service-client-library-wcf-data-services.md)」を参照してください。  
  
 他の種類のクライアントアプリケーションで[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードを利用するために使用できるプログラミングライブラリが用意されています。 詳細については、 [ODATA SDK](https://go.microsoft.com/fwlink/?LinkId=185796)を参照してください。  
  
## <a name="see-also"></a>関連項目

- [データ サービス リソースへのアクセス](accessing-data-service-resources-wcf-data-services.md)
- [クイック スタート](quickstart-wcf-data-services.md)
