---
title: ファイルとその他のソースからデータを読み込む
description: このハウツーでは、処理とトレーニング用のデータを ML.NET に読み込む方法について説明します。 データは、もともとはファイルか、またはデータベース、JSON、XML、メモリ内コレクションなどのその他のデータソースに格納されています。
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 4008f38bf4a20113a3f5c865e38222e5b82f2acc
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991361"
---
# <a name="load-data-from-files-and-other-sources"></a>ファイルとその他のソースからデータを読み込む

このハウツーでは、処理とトレーニング用のデータを ML.NET に読み込む方法について説明します。 データは、もともとはファイルか、またはデータベース、JSON、XML、メモリ内コレクションなどのその他のデータソースに格納されています。

## <a name="create-the-data-model"></a>データ モデルを作成する

ML.NET を使用すると、クラスを介してデータ モデルを定義できます。 たとえば、次のような入力データがあるとします。

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

以下のスニペットを表すデータ モデルを作成します。

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a>列属性を使用してデータ モデルに注釈を付ける

属性を使用すると、データ モデルとデータ ソースについてより多くの情報を ML.NET に与えられます。

[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 属性では、プロパティの列インデックスを指定します。

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) は、ファイルからデータを読み込む場合にのみ必要です。

列は次のように読み込みます。

- `HousingData` クラスの `Size` や `CurrentPrices` のように個々の列。
- `HousingData` クラスの `HistoricalPrices` のようにベクター形式で一度に複数の列。

ベクター プロパティがある場合は、データ モデルのプロパティに [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 属性を適用します。 ベクター内のすべての要素は同じ型にする必要がある点に注意してください。 列を分割したままにすると、特徴エンジニアリングが容易になり、柔軟性が向上しますが、列数が非常に多い場合、個々の列を操作するとトレーニング速度に影響します。

ML.NET は列名を介して動作します。 列の名前をプロパティ名以外に変更する場合は、[`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 属性を使用します。 メモリ内オブジェクトを作成するときも、プロパティ名を使ってオブジェクトを作成します。 ただし、データ処理と機械学習モデルの構築の場合、ML.NET では [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 属性に指定された値でプロパティがオーバーライドされ、参照されます。

## <a name="load-data-from-a-single-file"></a>1 つのファイルからデータを読み込む

ファイルからデータを読み込むには、読み込むデータのデータ モデルと共に [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) メソッドを使用します。 `separatorChar` パラメーターは既定でタブ区切りなので、必要に応じてデータ ファイルに合わせて変更します。 ファイルにヘッダーがある場合は、ファイルの最初の行を無視して 2 行目からデータの読み込みを開始するように、`hasHeader` パラメーターを `true` に設定します。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>複数のファイルからデータを読み込む

データが複数のファイルに格納されている場合、データ スキーマが同じである限り、ML.NET では、同じディレクトリまたは複数のディレクトリ内にある複数のファイルからデータを読み込むことができます。

### <a name="load-from-files-in-a-single-directory"></a>1 つのディレクトリ内のファイルから読み込む

すべてのデータ ファイルが同じディレクトリ内にある場合は、[`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) メソッドでワイルドカードを使用します。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>複数のディレクトリ内にあるファイルから読み込む

複数のディレクトリからデータを読み込むには、[`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) メソッドを使用して [`TextLoader`](xref:Microsoft.ML.Data.TextLoader) を作成します。 次に、[`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) メソッドを使用して個々のファイル パスを指定します (ワイルドカードは使用できません)。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>リレーショナル データベースからデータを読み込む

> [!NOTE]
> DatabaseLoader は現在のところ、プレビュー段階です。 [Microsoft.ML.Experimental](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview) および [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) NuGet パッケージを参照することで使用できます。

ML.NET では、SQL Server、Azure SQL Database、Oracle、SQLite、PostgreSQL、Progress、IBM DB2 など数多くの、[`System.Data`](xref:System.Data) でサポートされている多様なリレーショナル データベースからのデータの読み込みがサポートされています。

`House` という名前のテーブルと、次のスキーマが指定されたデータベースがあるとします。

```SQL
CREATE TABLE [House] (
    [HouseId] int NOT NULL IDENTITY,
    [Size] real NOT NULL,
    [Price] real NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

データは `HouseData` などのクラスでモデル化できます。

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float Price { get; set; }
}
```

次に、アプリケーション内で `DatabaseLoader` を作成します。

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

接続文字列と、データベースで実行される SQL コマンドを定義して、`DatabaseSource` インスタンスを作成します。 このサンプルでは、LocalDB の SQL Server データベースをファイル パスと共に使用します。 ただし、DatabaseLoader では、オンプレミスとクラウドのデータベースに対して、その他のすべての有効な接続文字列がサポートされています。

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size,Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance,connectionString,sqlCommand);
```

最後に、`Load` メソッドを使用して [`IDataView`](xref:Microsoft.ML.IDataView) にデータを読み込みます。

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>その他のソースからデータを読み込む

ファイル内の格納データの読み込みに加え、ML.NET では、以下のようなソースからのデータの読み込みがサポートされています。

- メモリ内コレクション
- JSON/XML

ストリーミング ソースを使用する場合、ML.NET では入力がメモリ内コレクション形式であると想定される点に注意してください。 そのため、JSON/XML などのソースを使用するときは、必ずデータをメモリ内コレクション形式にします。

次のメモリ内コレクションがあるとします。

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) メソッドを使用してメモリ内コレクションを [`IDataView`](xref:Microsoft.ML.IDataView) に読み込みます。

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) では、この読み込み元の [`IEnumerable`](xref:System.Collections.IEnumerable) がスレッドセーフであると想定されています。

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
