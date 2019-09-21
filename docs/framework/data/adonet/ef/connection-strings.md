---
title: ADO.NET Entity Framework の接続文字列
ms.date: 10/15/2018
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
ms.openlocfilehash: 8c583d74dd3b1b8322fa8ea884092f8eb893af6a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251653"
---
# <a name="connection-strings-in-the-adonet-entity-framework"></a>ADO.NET Entity Framework の接続文字列

接続文字列には、データ プロバイダーからデータ ソースにパラメーターとして渡す初期化情報が含まれています。 接続文字列は接続を開くときに解析され、その構文はデータ プロバイダーによって異なります。 Entity Framework で使用される接続文字列には、Entity Framework のサポート基盤である ADO.NET データ プロバイダーへの接続に使用される情報が含まれています。 また、必要なモデル ファイルおよびマッピング ファイルに関する情報も含まれています。

接続文字列は、モデル メタデータおよびマッピング メタデータにアクセスしてデータ ソースに接続する際に EntityClient プロバイダーによって使用されます。 接続文字列へのアクセスや接続文字列の設定は、<xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> の <xref:System.Data.EntityClient.EntityConnection> プロパティを使用して行います。 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> クラスを使用すると、接続文字列内のパラメーターの構築やこれらへのアクセスをプログラムで行えます。 詳細については、「[方法 :EntityConnection 接続文字列](how-to-build-an-entityconnection-connection-string.md)を作成します。

[Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))は、アプリケーションの構成ファイルに格納されている接続文字列を生成します。 <xref:System.Data.Objects.ObjectContext> は、オブジェクト クエリの作成時に自動的にこの接続情報を取得します。 <xref:System.Data.EntityClient.EntityConnection> インスタンスで使用される <xref:System.Data.Objects.ObjectContext> には、<xref:System.Data.Objects.ObjectContext.Connection%2A> プロパティからアクセスできます。 詳細については、「[接続とトランザクションの管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))」を参照してください。

## <a name="connection-string-syntax"></a>接続文字列の構文

接続文字列の一般的な構文の詳細については、「[接続文字列の構文 |」を参照してください。ADO.NET の接続文字列](../connection-strings.md#connection-string-syntax)。

## <a name="connection-string-parameters"></a>接続文字列パラメーター

<xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> のキーワード値に有効な名前を次の表に示します。

|キーワード|説明|
|-------------|-----------------|
|`Provider`|`Name` キーワードが指定されていない場合に必要です。 基になるプロバイダーの <xref:System.Data.Common.DbProviderFactory> オブジェクトを取得するために使用されるプロバイダー名です。 この値は定数です。<br /><br /> `Name` キーワードがエンティティ接続文字列に含まれていない場合、`Provider` キーワードの空でない値が必要になります。 このキーワードは `Name` キーワードと同時に指定できません。|
|`Provider Connection String`|省略可能です。 基になるデータ ソースに渡される、プロバイダー固有の接続文字列を指定します。 この接続文字列には、データプロバイダーの有効なキーワードと値のペアが含まれています。 無効な `Provider Connection String` がデータ ソースによって評価されると、ランタイム エラーが発生します。<br /><br /> このキーワードは `Name` キーワードと同時に指定できません。<br /><br /> [ADO.NET 接続文字列](../connection-strings.md)の一般的な構文に従って、必ず値をエスケープしてください。 例と`Server=serverName; User ID = userID`して、次の接続文字列を考えてみましょう。 セミコロンが含まれているため、エスケープする必要があります。 二重引用符が含まれていないため、エスケープに使用できます。<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`|
|`Metadata`|`Name` キーワードが指定されていない場合に必要です。 メタデータとマッピング情報の検索対象となるディレクトリ、ファイル、およびリソースの場所をパイプで区切って指定したリストです。 次に例を示します。<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> パイプ区切り記号の両側の空白は無視されます。<br /><br /> このキーワードは `Name` キーワードと同時に指定できません。|
|`Name`|アプリケーションは、オプションで、必要なキーワード/値接続文字列値を提供する接続名をアプリケーション構成ファイル内で指定できます。 その場合は、接続文字列内に値を直接記述することはできません。 `Name` キーワードは、構成ファイル内で使用できません。<br /><br /> `Name` キーワードが接続文字列に含まれていない場合、Provider キーワードの空でない値が必要になります。<br /><br /> このキーワードは他のすべての接続文字列キーワードと同時に指定できません。|

アプリケーション構成ファイルに格納されている[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)の接続文字列の例を次に示します。

## <a name="model-and-mapping-file-locations"></a>モデル ファイルおよびマッピング ファイルの場所

`Metadata` パラメーターには、`EntityClient` プロバイダーがモデル ファイルおよびマッピング ファイルを検索するための場所のリストが格納されます。 多くの場合、モデル ファイルとマッピング ファイルは、アプリケーション実行可能ファイルと同じディレクトリに配置されます。 これらのファイルは、特定の場所に配置することも組み込みリソースとしてアプリケーションに含めることもできます。

組み込みリソースは次のように指定します。

```
Metadata=res://<assemblyFullName>/<resourceName>.
```

組み込みリソースの場所を定義するには、次のオプションを使用できます。

|オプション|説明|
|-|-|
|`assemblyFullName`|リソースが組み込まれたアセンブリの完全な名前。 この名前には、次のように単純な名前、バージョン名、サポートされるカルチャ、および公開キーが含まれます。<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> リソースは、アプリケーションからアクセスできる任意のアセンブリに組み込むことができます。<br /><br /> \*に`assemblyFullName`ワイルドカード () を指定した場合、Entity Framework ランタイムは次の場所にあるリソースをこの順序で検索します。<br /><br /> 1.呼び出し側のアセンブリ<br />2.参照アセンブリ<br />3.アプリケーションの bin ディレクトリ内のアセンブリ<br /><br /> ファイルが上記のどの場所にもない場合は、例外がスローされます。 **注:** ワイルドカード (*) を使用する場合、Entity Framework では、正しい名前のリソースを見つけるためにすべてのアセンブリを調べる必要があります。 パフォーマンスを向上させるには、ワイルドカードではなくアセンブリ名を指定してください。|
|`resourceName`|インクルードされたリソースの名前 (Adventureworksmodel.edmx など)。 メタデータ サービスでは、拡張子が .csdl、.ssdl、または .msl のいずれかであるファイルまたはリソースのみが検索されます。 `resourceName` を指定しない場合は、すべてのメタデータ リソースが読み込まれます。 リソースには、アセンブリ内で一意の名前を付ける必要があります。 同じ名前が付けられた複数のファイルがアセンブリ内の異なるディレクトリで定義されている場合、`resourceName` には、リソースの名前の前にフォルダー構造を含める必要があります (FolderName.FileName.csdl など)。<br /><br /> `resourceName` にワイルドカード (*) を指定した場合、`assemblyFullName` は不要です。|

> [!NOTE]
> パフォーマンスを向上させるには、リソースを呼び出し側のアセンブリに組み込んでください。ただし、呼び出し側のアセンブリ内の基になるマッピング ファイルとメタデータ ファイルへの参照が存在しない Web 以外のシナリオの場合は除きます。

次の例では、呼び出し側のアセンブリ、参照アセンブリ、およびアプリケーションの bin ディレクトリ内のその他のアセンブリに存在するすべてのモデル ファイルおよびマッピング ファイルを読み込みます。

```
Metadata=res://*/
```

次の例では、model.csdl ファイルを AdventureWorks アセンブリから読み込み、model.ssdl ファイルと model.msl ファイルを実行中のアプリケーションの既定のディレクトリから読み込みます。

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl
```

次の例では、指定した 3 つのリソースを特定のアセンブリから読み込みます。

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl
```

次の例では、拡張子が .csdl、.msl、および .ssdl であるすべての組み込みリソースをアセンブリから読み込みます。

```
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/
```

次の例では、読み込まれたアセンブリの場所から、相対ファイルパスの\\すべてのリソースと "datadir\ metadata" を読み込みます。

```
Metadata=datadir\metadata\
```

次の例では、相対ファイル パス内のすべてのリソースを読み込まれたアセンブリの場所から読み込みます。

```
Metadata=.\
```

## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>&#124;DataDirectory&#124;代替文字列と Web アプリケーションルート演算子 (~) のサポート

`DataDirectory`~ 演算子は、 <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>キーワード`Metadata`と`Provider Connection String`キーワードの一部としてで使用されます。 <xref:System.Data.EntityClient.EntityConnection> によって、`DataDirectory` と ~ 演算子がそれぞれ <xref:System.Data.Metadata.Edm.MetadataWorkspace> とストア プロバイダーに転送されます。

|用語|説明|
|----------|-----------------|
|`&#124;DataDirectory&#124;`|マッピング ファイルとメタデータ ファイルの相対パスに解決されます。 この値は、`AppDomain.SetData("DataDirectory", objValue)` メソッドで設定される値です。 置換`DataDirectory`文字列は、パイプ文字で囲む必要があります。また、名前とパイプ文字の間に空白を置くことはできません。 `DataDirectory` の名前では大文字と小文字は区別されません。<br /><br /> "DataDirectory" という名前の物理ディレクトリをメタデータパスの一覧のメンバーとして渡す必要がある場合は、名前の両側または両方に空白を追加します。 たとえば、`Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"` のように指定します。 ASP.NET アプリケーションは、 &#124;DataDirectory&#124;を "\<application root >/app_data" フォルダーに解決します。|
|~|Web アプリケーション ルートに解決されます。 先頭の ~ 文字は、有効なローカル サブディレクトリを表すこともありますが、常に Web アプリケーション ルート演算子 (~) として解釈されます。 このようなローカル サブディレクトリを参照するには、ユーザーが明示的に `./~` を渡す必要があります。|

`DataDirectory` と ~ 演算子は、パスの先頭にのみ指定する必要があります。その他の位置では解決されません。 Entity Framework では、`~/data` の解決は試行されますが、`/data/~` は物理パスとして処理されます。

`DataDirectory` または ~ 演算子で始まるパスは、`DataDirectory` と ~ 演算子の分岐の外側の物理パスには解決できません。 たとえば、パス `~`、`~/data`、`~/bin/Model/SqlServer` は解決されます。 パス `~/..` や `~/../other` は解決できません。

`DataDirectory` と ~ 演算子は、`|DataDirectory|\Model` や `~/bin/Model` など、サブディレクトリが含まれるように拡張できます。

`DataDirectory` 置換文字列と ~ 演算子の解決は非再帰型です。 たとえば、`DataDirectory` に `~` 文字が含まれる場合は、例外が発生します。 これにより、無限再帰が回避されます。

## <a name="see-also"></a>関連項目

- [データ プロバイダーの操作](working-with-data-providers.md)
- [配置に関する注意事項](deployment-considerations.md)
- [接続とトランザクションの管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [接続文字列](../connection-strings.md)
