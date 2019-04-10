---
title: '方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 01a27c21948e3030059ddd1416d8c7727ac6435c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194462"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする
Svcutil.exe を使用すると、実行中のサービスからメタデータをダウンロードして、ローカル ファイルに保存できます。 HTTP および HTTPS の URL スキームの場合、Svcutil.exe が Ws-metadataexchange を使用してメタデータを取得しようと[XML Web サービス探索](https://go.microsoft.com/fwlink/?LinkId=94950)します。 その他の URL スキームの場合、Svcutil.exe は WS-MetadataExchange のみを使用します。  
  
 既定で、Svcutil.exe は <xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスに定義されているバインディングを使用します。 WS-MetadataExchange で使用するバインディングを構成するには、Svcutil.exe の構成ファイル (svcutil.exe.config) でクライアント エンドポイントを定義する必要があります。このとき、クライアント エンドポイントが `IMetadataExchange` コントラクトを使用し、メタデータ エンドポイントのアドレスの URI (Uniform Resource Identifier) スキームと同じ名前を持つように定義します。  
  
> [!CAUTION]
> 同じ名前の操作を含む各コントラクトの 2 つの異なるサービスを公開するサービスのメタデータを取得する Svcutil.exe を実行していると、Svcutil.exe では「メタデータを取得できませんから...」という、エラーが表示されます。というサービス コントラクトを公開するサービスがある場合など`ICarService`操作を持つ`Get(Car c)`と同じサービスというサービス コントラクトを公開します`IBookService`操作を持つ`Get(Book b)`します。 この問題を回避するには、次のいずれかの操作を実行します。
>
> - 操作の名前を変更する。
> - <xref:System.ServiceModel.OperationContractAttribute.Name%2A> を別の名前に設定する。
> - <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティを使用して、操作の名前空間のいずれかを別の名前空間に設定する。
  
## <a name="to-download-metadata-using-svcutilexe"></a>Svcutil.exe を使用してメタデータをダウンロードするには  
  
1.  次の場所で Svcutil.exe ツールを検索します。  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  コマンド プロンプトで、次の形式を使用してツールを起動します。  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     メタデータをダウンロードするには `/t:metadata` オプションを指定する必要があります。 このオプションを指定しないと、クライアントのコードと構成が生成されます。  
  
3.  <`url`> 引数のメタデータを提供するサービス エンドポイントまたはオンラインでホストされているメタデータ ドキュメントの URL を指定します。 <`epr`> WS アドレス指定を含む XML ファイルへのパスを指定する引数`EndpointAddress`Ws-metadataexchange をサポートするサービスのエンドポイント。  
  
 このツールを使用して、メタデータのダウンロードの詳細についてより多くのオプションを参照してください。 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。  
  
## <a name="example"></a>例  
 次のコマンドにより、実行中のサービスからメタデータ ドキュメントがダウンロードされます。  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>関連項目

- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
