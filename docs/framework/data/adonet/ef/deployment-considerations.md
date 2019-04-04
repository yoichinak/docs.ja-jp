---
title: 配置に関する注意事項 (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: 683f5e9b43bceb09d6354079fd9f7fcb7ed09eac
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828086"
---
# <a name="deployment-considerations-entity-framework"></a>配置に関する注意事項 (Entity Framework)
このトピックでは、データ アクセスに ADO.NET Entity Framework を使用するアプリケーションの配置について説明します。 Entity Framework の詳細については、[Getting Started](../../../../../docs/framework/data/adonet/ef/getting-started.md)を参照してください。  
  
 Entity Framework は、Visual Studio に組み込むことにより Visual Studio での開発を容易にする一連のツールを提供します。 詳細については、[ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))を参照してください。 このトピックでは、Entity Framework ベースのアプリケーションを配置するための具体的なテクノロジの使用法については触れません。  
  
 Visual Studio では、ClickOnce 配置など、アプリケーションの配布および配置のための機能が提供されています。 詳細については、次を参照してください。[アプリケーションの配置とコンポーネント](/visualstudio/deployment/deploying-applications-services-and-components)、Visual Studio ドキュメント。  
  
 Entity Framework を使用するアプリケーションを配置する場合は、次の注意事項が適用されます。  
  
-   .NET Framework 3.5 Service Pack 1 (SP1) 以降、Entity Framework は .NET Framework のコンポーネントになっています。 Entity Framework ベースのアプリケーションを配置する場合は、.NET Framework 3.5 SP1 以降のバージョンがインストールされていることを確認する必要があります。  
  
-   Entity Data Model ウィザードで概念モデルが生成されると、アプリケーション設定ファイルに接続文字列が作成されます。 モデル ファイルおよびマッピング ファイルをアプリケーション リソースとして埋め込むか、出力ディレクトリにコピーすることができます。 既定では、モデル ファイルとマッピング ファイルは、組み込みアプリケーション リソースとして配置されます。 エンティティ デザイナー ファイルの `Metadata Artifact Processing` プロパティを使用して、次のオプションのいずれかを選択することができます。 詳細については、「[方法 :モデルをコピーするファイルとマッピング ファイルを出力ディレクトリに](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716709(v=vs.100))します。  
  
-   モデルとマッピングの情報 (概念スキーマ定義言語 (CSDL)、ストア スキーマ定義言語 (SSDL)、およびマッピング仕様言語 (MSL) で表現) は、アプリケーションと共に配置され、その場所は、接続文字列によって指定されます。 詳細については、「[Connection Strings (接続文字列)](../../../../../docs/framework/data/adonet/ef/connection-strings.md)」をご覧ください。  
  
-   モデルとマッピングの情報をアプリケーション リソースとして組み込む場合は、概念モデルを更新するたびに、アプリケーションの再コンパイルと再配置が必要になります。  
  
-   Entity Framework は .NET Framework のコンポーネントであるため、.NET Framework 使用許諾契約書での許可に従ってアプリケーションと共に再配布できます。  
  
## <a name="see-also"></a>関連項目
- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
- [開発および配置に関する注意事項](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
