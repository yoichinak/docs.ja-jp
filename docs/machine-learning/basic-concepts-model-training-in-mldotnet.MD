---
title: ML.NET でのモデル トレーニングに関する基本的な概念
description: この記事では、ML.NET での "*モデル トレーニング*" シナリオに関する基本概念について説明します。 よりシンプルなシナリオである "*既存モデルでの予測*" と関係のない概念も含まれます。
ms.date: 03/05/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 78554cfd1dfdb3dba82a325d47245aeb313bb6fe
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675564"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a>ML.NET でのモデル トレーニングに関する基本的な概念

この記事では、ML.NET での "*モデル トレーニング*" シナリオに関する基本概念について説明します。 よりシンプルなシナリオである "*既存モデルでの予測*" と関係のない概念も含まれます。

この記事と関連サンプルでは、現時点では **ML.NET バージョン 0.10** が使用されています。 詳細については、リリース ノート ([GitHub リポジトリの dotnet/machinelearning ](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)) を参照してください。

## <a name="model-training-concepts"></a>モデルのトレーニングの概念

このドキュメントでは、ML.NET でのモデルのトレーニングに関連する次の概念について説明します。

- `IDataView` インターフェイスとして表された "[*データ*](#data)"。
  - ML.NET では、データは SQL ビューに似ています。つまり、遅延評価で、不変で、カーソル可能で、異種で、スキーマ化されたデータセットです。 
  - データ インターフェイスに関する優れたドキュメントとしては、「[IDataView Design Principles](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md)」(IDataView 設計原則) をご覧ください。
- `ITransformer` インターフェイスとして表された "[*トランスフォーマー*](#transformer)"。
  - トランスフォーマーは、データを受け取り、データに対して何らかの作業を行い、変換された新しいデータを返すコンポーネントです。
  - たとえば、機械学習モデルは特徴を受け取って予測を返すトランスフォーマーと考えることができます。
  - 別の例としては、テキスト トークナイザーは 1 つのテキスト列を受け取り、テキストから抽出された個々の単語を含むベクトル列を出力します。
- `IDataReader<T>` インターフェイスとして表された "[*データ リーダー*](#data-reader)"。
  - データ リーダーは、データを作成する ML.NET コンポーネントです。 `T` のインスタンスを受け取り、そのデータを返します。 
  - たとえば、*TextLoader* は `IDataReader<IMultiStreamSource>` です。 これはソースを受け取って、データを生成します。 
- `IEstimator<T>` インターフェイスとして表された "[*エスティメーター*](#estimator)"。
  - これは、データから学習するオブジェクトです。 学習の結果は "*トランスフォーマー*" です。
  - 機械学習の "*アルゴリズム*" は、データについて学習して機械学習の "*モデル*" を生成するエスティメーターと考えることができます。
- `PredictionEngine<TSrc, TDst>` クラスとして表された "[*予測関数*](#prediction-function)"。
  - 予測関数は、予測時などに 1 つの行に対してトランスフォーマーを適用するマシンと見なすことができます。

## <a name="data"></a>データ

ML.NET では、データは SQL ビューに似ています。つまり、遅延評価で、カーソル可能で、異種で、スキーマ化されたデータセットです。

- データ ビューの列に関する情報を含む "*スキーマ*" (`ISchema` インターフェイスのインスタンス) を持っています。
  - 各列には、"*名前*"、"*型*"、および列に関連付けられた "*メタデータ*" の任意のセットがあります。
  - 列の "*メタデータ*" には、ベクトルの列のスロット名のような情報が含まれています。 メタデータ自体は、各列に固有の別の 1 つの行 "*データ*" として表されます。
  - データ ビューは "*カーソル*" のソースです。 SQL のカーソルを考えてください。カーソルは、一度に 1 行ずつデータを反復処理するオブジェクトであり、使用可能なデータを表します。
  - 当然ながら、データには必要なだけいくつでもアクティブなカーソルを作成できます。 データ自体は変更不可能であるため、カーソルは完全に独立しています。
  - 通常、カーソルは列のサブセットにのみアクセスします。効率化するため、ML.NET ではカーソルで必要な列の値のみが計算されます。

## <a name="transformer"></a>トランスフォーマー

トランスフォーマーは、データを受け取り、データに対して何らかの作業を行い、変換された新しいデータを返すコンポーネントです。

ML.NET のほとんどのトランスフォーマーは、多くの場合、一度に 1 つの "*入力列*" を処理して、"*出力列*" を生成します。 たとえば、`new HashTransformer("bar", "foo")` は、"foo" 列から値を取得し、そのハッシュ値を計算して、"bar" 列に格納します。 

また、入力列と出力列は同じ名前であることが一般的です。 この場合、古い列は新しい列で置き換えられます。 たとえば、`new HashTransformer("foo")` は、"foo" 列から値を取得し、そのハッシュ値を計算して、"foo" 列に戻します。 

`Transform` が呼び出されると、任意のトランスフォーマーによって新しいデータ ビューが生成されます。 データ ビューは不変であることを思い出してください。

もう 1 つの重要な考慮事項は、データは遅延評価されるため、"*トランスフォーマーも遅延である*" ということです。 基本的に、次の呼び出しの後で

```csharp
var newData = transformer.Transform(oldData)
```

実際の計算は行われません。 `newData` からカーソルを取得し、値の使用を開始した後でのみ、`newData` によって `transformer` の変換ロジックが呼び出されます (ただし、これは、要求された列を生成するために対象の `transformer` が必要な場合にのみ行われます)。

### <a name="transformer-chains"></a>トランスフォーマーのチェーン

トランスフォーマーの便利な性質は、"*トランスフォーマーのシーケンシャルな適用を別のトランスフォーマーでビルドできる*" というものです。

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

この性質は ML.NET でよく使用されます。通常、トレーニング済みの ML.NET モデルはトランスフォーマーのチェーンであり、これはすべての意図と目的に対する 1 つの "*トランスフォーマー*" です。

## <a name="data-reader"></a>データ リーダー

データ リーダーは、データを "作成する" ための ML.NET コンポーネントです。このコンポーネントでは、`T` のインスタンスが取得され、そのデータが返されます。

注意すべき興味深い性質は、既存のデータ リーダーにトランスフォーマーをアタッチすることにより、データ リーダーを作成できることです。 このようにして、トランスフォーマーの動作が組み込まれたリーダーを作成できます。

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

トランスフォーマーと似ているもう 1 つの点は、データは遅延評価されるため、"*リーダーも遅延である*" ことです。`reader.Read()` を呼び出した時点では、実際の "読み取り" はまったく (または最小限でしか) 行われません。結果のデータでカーソルが要求されたときにのみ、リーダーは処理を開始します。

## <a name="estimator"></a>エスティメーター

"*エスティメーター*" は、データから学習するオブジェクトです。 学習の結果は "*トランスフォーマー*" です。

ML.NET では、この特性を使用して、異なるエスティメーターを連結する学習パイプラインを作成します。

```csharp
MLContext mlContext = new MLContext(seed: 0);

var pipeline = mlContext.Transforms.CopyColumns("Label","FareAmount")
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("VendorId"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("RateCode"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("PaymentType"))
    .Append(mlContext.Transforms.Concatenate("Features","VendorId","RateCode","PassengerCount","TripTime","TripDistance","PaymentType"))
    .Append(mlContext.Regression.Trainers.FastTree("Label","Features"));

var model = pipeline.Fit(dataView);
```

エスティメーターの 1 つの重要な特性は、"*エスティメーターは遅延ではなく一括である*" ということです。`Fit` のすべての呼び出しによって学習が発生し、その操作には時間がかかる可能性があります。

## <a name="prediction-function"></a>予測関数

予測関数は、1 つの行に対してトランスフォーマーを適用するコンポーネントと見なすことができます。

モデルを取得した後は (`Fit()` によってトレーニングされたか、またはどこかから読み込まれた "*トランスフォーマー*")、それを使用して、`model.Transform(data)` の通常の呼び出しで予測を行うことができます。 ただし、実際のシナリオでこのモデルを使用するときは、通常、予測に多くの例を使用しません。 代わりに、一度に 1 つの例を使用し、すぐに適切なタイミングで予測を行う必要があります。

もちろん、これをバッチ予測に軽減できます。

- 厳密に 1 つの行でデータ ビューを作成します。
- `model.Transform(data)` を呼び出して、予測されたデータ ビューを取得します。
- 結果のデータに対するカーソルを取得します。
- カーソルを 1 ステップ進めて、最初の (そして唯一の) 行を取得します。
- それから予測される値を抽出します。

前記のアルゴリズムは、次のように[スキーマの理解](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md)と 2 つのユーザー定義オブジェクト `InputExample` と `OutputPrediction` を使用して実装できます。

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

ただし、これは面倒で、パフォーマンス コストがかかります。 代わりに、予測関数オブジェクトでは、拡張メソッド `CreatePredictionEngine` により同じ処理が、ただしもっと速く便利に行われます。

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

予測関数は "*再入可能/スレッド セーフではありません*"。 複数のスレッドで同時に予測を実行する場合は、スレッドごとに予測関数が存在する必要があります。
