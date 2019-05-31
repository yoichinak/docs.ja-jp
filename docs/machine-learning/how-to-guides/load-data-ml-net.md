---
title: データを読み込む
description: データ ファイルとストリーミング データを ML.NET に読み込む
ms.date: 05/03/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 6edcc92b610e2e1f5e21c371b9f0aefd0b216d31
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063645"
---
# <a name="load-data-from-file-and-in-memory-sources"></a>ファイルとメモリ内のソースからデータを読み込む

このハウツーでは、処理とトレーニング用のデータを ML.NET に読み込む方法について説明します。 データは、もともとファイルに格納されていたか、リアルタイム/ストリーミング データ ソースです。

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

ベクター プロパティがある場合は、データ モデルのプロパティに [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 属性を適用します。 ベクター内のすべての要素は同じ型にする必要がある点に注意してください。

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

## <a name="load-data-from-a-streaming-source"></a>ストリーミング ソースからデータを読み込む

ディスク上の格納データの読み込みに加え、ML.NET は、以下のようにさまざまなストリーミング ソースからのデータの読み込みをサポートします。

- メモリ内コレクション
- JSON/XML
- データベース

> [!IMPORTANT]
> ストリーミング ソースを使用する場合、ML.NET では入力がメモリ内コレクション形式であると想定される点に注意してください。 そのため、JSON/XML などのソースを使用するときは、必ずデータをメモリ内コレクション形式にします。

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

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
