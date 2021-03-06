---
title: "EDM ジェネレーター (EdmGen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d310786a12aa538a8a820c1c05788f30fe28c44
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="edm-generator-edmgenexe"></a>EDM ジェネレーター (EdmGen.exe)
EdmGen.exe は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] モデルとマッピング ファイルを操作するためのコマンドライン ツールです。 EdmGen.exe ツールを使用すると、次の操作を行うことができます。  
  
-   データ ソース固有の .NET Framework データ プロバイダーを使用してデータ ソースに接続し、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で使用される概念モデル (.csdl)、ストレージ モデル (.ssdl)、およびマッピング (.msl) のファイルを生成する。 詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルの生成に使用する EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)です。  
  
-   既存のモデルを検証する。 詳細については、次を参照してください。[する方法: モデルの検証とマッピング ファイルを使用して EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)です。  
  
-   概念モデル (.csdl) ファイルから生成されたオブジェクト クラスを含む C# コード ファイルまたは Visual Basic コード ファイルを生成する。 詳細については、次を参照してください。[する方法: オブジェクトレイヤー コードの生成に使用する EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)です。  
  
-   事前に生成した既存のモデルのビューを含む C# コード ファイルまたは Visual Basic コード ファイルを生成する。 詳細については、[する方法: クエリ パフォーマンスを向上させる Pre-Generate ビュー](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)です。  
  
 EdmGen.exe ツールは [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] ディレクトリにインストールされます。 多くの場合、C:\windows\Microsoft.NET\Framework\v4.0 にあります。 64 ビット システムの場合は、C:\windows\Microsoft.NET\Framework64\v4.0 にあります。 Visual Studio コマンド プロンプトから EdmGen.exe ツールをアクセスすることもできます (をクリックして**開始**、 をポイント**すべてのプログラム**、 をポイント**Microsoft Visual Studio 2010**、 をポイント**Visual Studio Tools**、クリックして**Visual Studio 2010 コマンド プロンプト**)。  
  
## <a name="syntax"></a>構文  
  
```  
EdmGen /mode:choice [options]  
```  
  
## <a name="mode"></a>モード  
 EdmGen.exe ツールを使用する場合、次のいずれかのモードを指定する必要があります。  
  
|モード|説明|  
|----------|-----------------|  
|`/mode:ValidateArtifacts`|.csdl、.ssdl、および .msl ファイルを検証し、エラーまたは警告を表示します。<br /><br /> このオプションを使用するには、少なくとも `/inssdl` 引数または `/incsdl` 引数のどちらかが必要です。 `/inmsl` を指定する場合は、`/inssdl` 引数と `/incsdl` 引数も必要です。|  
|`/mode:FullGeneration`|`/connectionstring` オプションで指定されたデータベース接続情報を使用し、.csdl、.ssdl、.msl、オブジェクト レイヤー、およびビュー ファイルを生成します。<br /><br /> このオプションを使用するには、`/connectionstring` 引数に加え、`/project` 引数を指定するか、`/outssdl`、`/outcsdl`、`/outmsdl`、`/outobjectlayer`、`/outviews`、`/namespace`、`/entitycontainer` の各引数を指定する必要があります。|  
|`/mode:FromSSDLGeneration`|指定された .ssdl ファイルから、.csdl ファイル、.msl ファイル、ソース コード、およびビューを生成します。<br /><br /> このオプションを使用するには、`/inssdl` 引数に加え、`/project` 引数を指定するか、`/outcsdl`、`/outmsl`、`/outobjectlayer`、`/outviews`、`/namespace,`、`/entitycontainer` の各引数を指定する必要があります。|  
|`/mode:EntityClassGeneration`|.csdl ファイルから生成されたクラスを含むソース コード ファイルを作成します。<br /><br /> このオプションを使用するには、`/incsdl` 引数に加え、`/project` 引数または `/outobjectlayer` 引数のどちらかを指定する必要があります。 `/language` 引数は省略可能です。|  
|`/mode:ViewGeneration`|.csdl、.ssdl、および .msl ファイルから生成されたビューを含むソース コード ファイルを作成します。<br /><br /> このオプションを使用するには、`/inssdl`、`/incsdl`、`/inmsl,` の各引数に加え、`/project` 引数または `/outviews` 引数のどちらかを指定する必要があります。 `/language` 引数は省略可能です。|  
  
## <a name="options"></a>オプション  
  
|オプション|説明|  
|------------|-----------------|  
|`/p[roject]:`\<string>|使用するプロジェクト名を指定します。 このプロジェクト名は、名前空間の設定の既定値、モデル ファイルとマッピング ファイルの名前、オブジェクト ソース ファイルの名前、およびビュー生成のソース ファイルの名前として使用されます。 設定されているエンティティ コンテナー名\<プロジェクト > コンテキスト。|  
|`/prov[ider]:`\<string>|ストレージ モデル (.ssdl) ファイルの生成に使用する [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] データ プロバイダーの名前です。 既定のプロバイダーは、 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>)。|  
|`/c[onnectionstring]:`\<接続文字列 >|データ ソースへの接続に使用する文字列を指定します。|  
|`/incsdl:`\<file>|.csdl ファイル、または .csdl ファイルがあるディレクトリを指定します。 この引数は複数回指定できるので、複数のディレクトリまたは .csdl ファイルを指定できます。 概念モデルが複数のファイルに分割されている場合にクラスの生成 (`/mode:EntityClassGeneration`) またはビューの生成 (`/mode:ViewGeneration`) を行うときは、複数のディレクトリを指定すると便利です。 また、複数のモデルを検証する (`/mode:ValidateArtifacts`) 場合にも役立ちます。|  
|`/refcsdl:`\<file>|追加の .csdl ファイル、またはソース .csdl ファイルの参照の解決に使用するファイルを指定します  (ソース .csdl ファイルは、`/incsdl` オプションで指定したファイルです)。 `/refcsdl` ファイルには、ソース .csdl ファイルが依存する型が含まれています。 この引数は複数回指定できます。|  
|`/inmsl:`\<file>|.msl ファイル、または .msl ファイルがあるディレクトリを指定します。 この引数は複数回指定できるので、複数のディレクトリまたは .msl ファイルを指定できます。 概念モデルが複数のファイルに分割されている場合にビューを生成 (`/mode:ViewGeneration`) するときは、複数のディレクトリを指定すると便利です。 また、複数のモデルを検証する (`/mode:ValidateArtifacts`) 場合にも役立ちます。|  
|`/inssdl:`\<file>|.ssdl ファイル、または .ssdl ファイルがあるディレクトリを指定します。 この引数は複数回指定できるので、複数のディレクトリまたは .ssdl ファイルを指定できます。 これは、複数のモデルを検証する場合 `(/mode:ValidateArtifacts)` に役立ちます。|  
|`/outcsdl:`\<file>|作成される .csdl ファイルの名前を指定します。|  
|`/outmsl:`\<file>|作成される .msl ファイルの名前を指定します。|  
|`/outssdl:`\<file>|作成される .ssdl ファイルの名前を指定します。|  
|`/outobjectlayer:`\<file>|.csdl ファイルから生成されたオブジェクトを含むソース コード ファイルの名前を指定します。|  
|`/outviews:`\<file>|生成されたビューを含むソース コード ファイルの名前を指定します。|  
|`/language:`[VB&#124;CSharp]|生成されるソース コード ファイルの言語を指定します。 既定の言語は C# です。|  
|`/namespace:`\<string>|使用するモデル名前空間を指定します。 名前空間は、`/mode:FullGeneration` または `/mode:FromSSDLGeneration` の実行時に .csdl ファイルに設定されます。 `/mode:EntityClassGeneration` の実行時には名前空間は使用されません。|  
|`/entitycontainer:`\<string>|生成されたモデル ファイルとマッピング ファイルの `<EntityContainer>` 要素に適用する名前を指定します。|  
|`/pl[uralize]`|単数形と複数形の英語のルールを、概念モデルの `Entity`、`EntitySet`、および `NavigationProperty` の各名前に適用します。 このオプションでは、以下の処理が実行されます。<br /><br /> -すべてのください`EntityType`単数形の名前。<br />-すべてのください`EntitySet`複数形の名前。<br />-ごと`NavigationProperty`最大で 1 つのエンティティを返す場合、名前の単数形です。<br />-ごと`NavigationProperty`が返すエンティティが 1 つ以上の場合、名前の複数形です。|  
|`/SupressForeignKeyProperties or /nofk`|外部キー列が概念モデルのエンティティ型のスカラー プロパティとして公開されないようにします。|  
|`/help` または `?`|このツールのコマンド構文とオプションを表示します。|  
|`/nologo`|著作権メッセージが表示されないようにします。|  
|`/targetversion:` \<string>|生成されたコードのコンパイルに使用される .NET Framework のバージョンです。 サポートされているバージョンは 4 と 4.5 です。 既定値は 4 です。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)  
  
 [方法: EdmGen.exe を使用してオブジェクトレイヤー コードを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)  
  
 [方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)  
  
## <a name="see-also"></a>参照  
 [ADO.NET Entity Data Model ツール](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)  
 [CSDL、SSDL、および MSL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
