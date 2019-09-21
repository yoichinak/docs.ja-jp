---
title: '方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 25840247e59b9dd61cadaa2ee94713240d135f88
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991613"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする
Svcutil.exe を使用すると、実行中のサービスからメタデータをダウンロードして、ローカル ファイルに保存できます。 HTTP および HTTPS の URL スキームの場合、Svcutil.exe は Ws-metadataexchange と[XML Web サービス探索](https://go.microsoft.com/fwlink/?LinkId=94950)を使用してメタデータを取得しようとします。 その他の URL スキームの場合、Svcutil.exe は WS-MetadataExchange のみを使用します。  
  
 既定で、Svcutil.exe は <xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスに定義されているバインディングを使用します。 WS-MetadataExchange で使用するバインディングを構成するには、Svcutil.exe の構成ファイル (svcutil.exe.config) でクライアント エンドポイントを定義する必要があります。このとき、クライアント エンドポイントが `IMetadataExchange` コントラクトを使用し、メタデータ エンドポイントのアドレスの URI (Uniform Resource Identifier) スキームと同じ名前を持つように定義します。  
  
> [!CAUTION]
> Svcutil.exe を実行して、それぞれに同じ名前の操作が含まれている2つの異なるサービスコントラクトを公開するサービスのメタデータを取得する場合、Svcutil.exe によって "メタデータを取得できません" というエラーが表示されます。たとえば`ICarService` 、操作`Get(Car c)`を持つという名前のサービスコントラクトを公開し、同じサービスが操作`Get(Book b)`を持つという名前`IBookService`のサービスコントラクトを公開するサービスがあるとします。 この問題を回避するには、次のいずれかの操作を実行します。
>
> - 操作の名前を変更する。
> - <xref:System.ServiceModel.OperationContractAttribute.Name%2A> を別の名前に設定する。
> - <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティを使用して、操作の名前空間のいずれかを別の名前空間に設定する。
  
## <a name="to-download-metadata-using-svcutilexe"></a>Svcutil.exe を使用してメタデータをダウンロードするには  
  
1. 次の場所で Svcutil.exe ツールを検索します。  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. コマンド プロンプトで、次の形式を使用してツールを起動します。  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     メタデータをダウンロードするには `/t:metadata` オプションを指定する必要があります。 このオプションを指定しないと、クライアントのコードと構成が生成されます。  
  
3. <`url`> 引数には、メタデータを提供するサービスエンドポイントの URL、またはオンラインでホストされているメタデータドキュメントを指定します。 <`epr`> 引数は、ws-metadataexchange をサポートするサービスエンドポイント`EndpointAddress`の ws-addressing を含む XML ファイルへのパスを指定します。  
  
 メタデータのダウンロードにこのツールを使用する方法の詳細については、「 [ServiceModel Metadata Utility tool (svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコマンドにより、実行中のサービスからメタデータ ドキュメントがダウンロードされます。  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>関連項目

- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
