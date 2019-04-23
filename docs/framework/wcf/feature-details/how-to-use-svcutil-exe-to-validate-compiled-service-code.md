---
title: '方法: Svcutil.exe を使用してコンパイル済みサービス コードを検証する'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 599f5624b7eb0c32cbcc0a78e6c7f989ce470b58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312424"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>方法: Svcutil.exe を使用してコンパイル済みサービス コードを検証する
使用することができます、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービスをホストせず、サービス実装と構成でエラーを検出します。  
  
### <a name="to-validate-a-service"></a>サービスを検証するには  
  
1. サービスを実行可能ファイルおよび 1 つ以上の依存アセンブリにコンパイルします。  
  
2. SDK コマンド プロンプトを開きます。  
  
3. コマンド プロンプトで、次の形式を使用して Svcutil.exe ツールを起動します。 さまざまなパラメーターの詳細については、の「サービスの検証を参照してください、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)トピック。  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     `/serviceName` オプションを使用して、検証するサービスの構成名を指定する必要があります。  
  
     `assemblyPath` 引数には、検証対象のサービスの実行可能ファイルへのパス、およびサービス型を格納している 1 つ以上のアセンブリへのパスを指定します。 実行可能アセンブリに、サービス構成を提供する関連構成ファイルが存在している必要があります。 標準のコマンドライン ワイルドカードを使用して、複数のアセンブリを指定できます。  
  
## <a name="example"></a>例  
 次のコマンドでは、myServiceHost.exe 実行可能ファイルに実装されたサービス myServiceName を検証します。  サービスの構成ファイル (myServiceHost.exe.config) は自動的に読み込まれます。  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>関連項目

- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
