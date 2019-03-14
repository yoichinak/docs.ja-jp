---
title: 機械学習データ変換 - ML.NET
description: ML.NET でサポートされている機能エンジニアリングのコンポーネントについて検証します。
author: JRAlexander
ms.custom: seodec18
ms.date: 01/14/2019
ms.openlocfilehash: e649c9a27f0409cb9cdfb554963b5c0e732991f2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355411"
---
# <a name="machine-learning-data-transforms---mlnet"></a>機械学習データ変換 - ML.NET

次の表には、ML.NET でサポートされているすべてのデータ変換に関する情報が含まれています。

> [!NOTE]
> ML.NET は現在プレビュー段階です。 現時点では、すべてのデータ変換がサポートされているわけではありません。 特定の変換に対するご要望を送信するには、[dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub リポジトリで問題をオープンしてください。

## <a name="combiners-and-segregators"></a>結合と分離

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.GroupTransform> | 連続するグループ ID に基づいて、スカラー列の値をベクターにグループ化します。 |
| <xref:Microsoft.ML.Transforms.UngroupTransform> | ベクター列をグループ解除して行のシーケンスにします。グループ化変換の逆です。 |

## <a name="conversions"></a>変換

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Conversions.HashingTransformer> | 単一の値の列またはベクター列のいずれかをハッシュします。 ベクター列の場合、スロットごとに個別にハッシュします。 これは、テキスト値またはキー値のいずれかをハッシュできます。 |
| <xref:Microsoft.ML.Transforms.Conversions.HashJoiningTransform> | 複数の列の値をハッシュに変換します。 この変換では、数値とテキストの両方の入力と、単一値とベクター値の両方の列を受け入れます。 |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToBinaryVectorMappingTransformer> | キーをバイナリ ベクター列に変換します。 |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToValueMappingTransformer > | KeyValues メタデータを使用してキー インデックスを KeyValues メタデータ内の対応する値にマップします。 |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToVectorMappingTransformer> | キーをベクター列に変換します。 |
| <xref:Microsoft.ML.Transforms.Conversions.TypeConvertingTransformer> | 型を指定した基になる列の型の変更は、変換できます。 |
| <xref:Microsoft.ML.Transforms.Conversions.ValueToKeyMappingTransformer> | 入力値 (単語、数字など) をディクショナリ内のインデックスに変換します。 |

## <a name="deep-learning"></a>ディープ ラーニング

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | 既存の ONNX モデルにデータを提供し、スコアを返します (予測)。 |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | 事前トレーニング済みの TensorFlow モデルを使用してスコア付けするか、TensorFlow モデルを再トレーニングすることができます。 |

## <a name="feature-extraction"></a>特徴抽出

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.CustomStopWordsRemovingTransform> | 個々のトークンをストップワードと比較 (大文字と小文字を区別しない比較) することで、ストップワードの指定されたリストを削除します。|
| <xref:Microsoft.ML.ImageAnalytics.ImageGrayscaleTransform> | 1 つまたは複数の ImageType 列を取得して、それらを同じイメージのグレースケール表現に変換します。|
| <xref:Microsoft.ML.ImageAnalytics.ImageLoaderTransform> | 1 つまたは複数の ReadOnlyMemory 列を取得し、それらを ImageType として読み込みます。 |
| <xref:Microsoft.ML.ImageAnalytics.ImagePixelExtractorTransform> | 1 つまたは複数の ImageType 列を取得して、それらをベクター表現に変換します。|
| <xref:Microsoft.ML.ImageAnalytics.ImageResizerTransform> | 1 つまたは複数の ImageType 列を取得して、それらを指定した高さと幅にサイズ変更します。|
| <xref:Microsoft.ML.Transforms.Text.LatentDirichletAllocationTransformer> | LightLDA (Latent Dirichlet Allocation の最新の実装) を実装します。|
| <xref:Microsoft.ML.Transforms.LoadTransform> | 指定したモデル ファイルから特定の変換を読み込みます。 シリアル化されたチェーンからの 'チェリー ピック' 変換を可能にしたり、事前トレーニング済みの変換を異なる (ただし互換性がある) データ ビューに適用することができます。 |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractingTransformer> | キーの指定のベクターで、n-gram のカウントのバッグ (長さ 1-n の連続する値のシーケンス) が生成されます。 n-gram のディクショナリをビルドし、ディクショナリの ID をバッグのインデックスとして使用することでこれを行います。 |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractorTransform> | トークン化されたテキスト (ReadOnlyMemory のベクター) のコレクション、またはキーのベクターを数値特徴ベクトルに変換します。 特徴ベクトルは n-gram のカウント (長さ 1-n の連続するトークン (単語またはキー) のシーケンス) です。 |
| <xref:Microsoft.ML.Transforms.Text.NgramHashExtractingTransformer> | ハッシュを使用して、トークン化されたテキスト (ReadOnlyMemory のベクター) のコレクションを数値特徴ベクトルに変換します。 |
| <xref:Microsoft.ML.Transforms.Text.NgramHashingTransformer> | 指定したテキストで、n-gram のカウントのバッグ (長さ 1-n の連続する単語のシーケンス) を生成します。 |
| <xref:Microsoft.ML.Transforms.Categorical.OneHotEncodingTransformer> | データに基づいてカテゴリのディクショナリをビルドし、ディクショナリ内の ID を配列内のインデックスとして使用することで、カテゴリ値をインジケーター配列に変換します。 |
| <xref:Microsoft.ML.Transforms.Projections.PcaTransform> | 特徴ベクトルの低ランク サブ空間へのプロジェクションを計算します。 |
| <xref:Microsoft.ML.Transforms.Text.SentimentAnalyzingTransformer> | 事前にトレーニングされたセンチメント モデルを使用して、入力文字列をスコア付けします。 |
| <xref:Microsoft.ML.Transforms.Text.StopWordsRemovingTransformer> | 個々のトークンをストップワードと比較 (大文字と小文字を区別しない比較) することで、ストップワード (最もよく使われている単語) の言語固有のリストを削除します。 |
| <xref:Microsoft.ML.Transforms.Text.WordBagBuildingTransformer> | 指定したテキストで、n-gram のカウントのバッグ (連続する単語のシーケンス) を生成します。 n-gram のディクショナリをビルドし、ディクショナリの ID をバッグのインデックスとして使用することでこれを行います。 |
| <xref:Microsoft.ML.Transforms.Text.WordHashBagProducingTransformer> | 指定したテキストで、n-gram のカウントのバッグ (長さ 1-n の連続する単語のシーケンス) を生成します。 n-gram ごとにハッシュし、ハッシュ値をバッグ内のインデックスとして使用することでこれを行います。 |
| <xref:Microsoft.ML.Transforms.Text.WordTokenizingTransformer> | 区切り文字を使用してテキストを単語に分割します。 |


## <a name="image-model-featurizers"></a>イメージ モデル フィーチャライザー

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.AlexNetExtension> | これは、事前トレーニング済みの [AlexNet](https://en.wikipedia.org/wiki/AlexNet) モデルを使用するために <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> で使用される拡張メソッドです。 この拡張を含む NuGet もバイナリ モデル ファイルが含まれることが保証されます。 |
| <xref:Microsoft.ML.Transforms.ResNet18Extension> | これは、事前トレーニング済みの ResNet18 モデルを使用するために <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> で使用される拡張メソッドです。 この拡張を含む NuGet もバイナリ モデル ファイルが含まれることが保証されます。 |
| <xref:Microsoft.ML.Transforms.ResNet50Extension> | これは、事前トレーニング済みの ResNet50model モデルを使用するために <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> で使用される拡張メソッドです。 この拡張を含む NuGet もバイナリ モデル ファイルが含まれることが保証されます。 |
| <xref:Microsoft.ML.Transforms.ResNet101Extension> | これは、事前トレーニング済みの ResNet101 モデルを使用するために <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> で使用される拡張メソッドです。 この拡張を含む NuGet もバイナリ モデル ファイルが含まれることが保証されます。 |

## <a name="label-parsing"></a>ラベルの解析

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.LabelConvertTransform> |  ラベルを変換します。 |
| <xref:Microsoft.ML.Transforms.LabelIndicatorTransform> | 主に OVA で使用するために、多クラス ラベルをバイナリ True、False ラベルに再マップします。|

## <a name="missing-values"></a>欠損値

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueDroppingTransformer> | 列から欠損値をドロップします。 |
| <xref:Microsoft.ML.Transforms.MissingValueIndicatorTransform> | 入力列と同じ数のスロットを持つブール値出力列を作成します。この場合、入力列に値がない場合、出力値は true です。 |
| <xref:Microsoft.ML.Transforms.MissingValueReplacingTransformer> | 欠損値は、既定値または平均値/最小値/最大値 (テキスト以外の列の場合のみ) のいずれかで置き換えることで処理します。 |

## <a name="normalization"></a>正規化

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Projections.LpNormalizingTransformer> | Lp-Norm (ベクター/行方向) 正規化変換。 |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarDblAggregator> | ベクター値列の平均と分散を計算します。 現在の平均と M2 (平均からの値の 2 乗差の合計)、NaNs の数、ゼロ以外の要素の数を追跡します。 |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarSngAggregator> | ベクター値列の平均と分散を計算します。 現在の平均と M2 (平均からの値の 2 乗差の合計)、NaNs の数、ゼロ以外の要素の数を追跡します。 |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxDblAggregator> | 最小値、最大値、非スパース値の数 (vCount)、およびベクター値列に対する ProcessValue() の呼び出し回数 (trainCount) を追跡します。 |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizeTransform> | 機能範囲を標準化します。 |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizingTransformer> |機能範囲を標準化します。 |

## <a name="onnx"></a>Onnx

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | ONNX standard v1.2 を使用する事前トレーニング済みの ONNX モデルにスコア付けします。 |

## <a name="preprocessing"></a>前処理
| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BootstrapSamplingTransformer> | ポアソン分布のサンプリングを使用してブートストラップのサンプリングの近似値を求めます。 |
| <xref:Microsoft.ML.Transforms.Projections.RandomFourierFeaturizingTransformer> | ランダムなフーリエ機能を生成します。 |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | テキストが文字のシーケンスと見なされる文字指向のトークナイザー。 |
| <xref:Microsoft.ML.Transforms.Projections.VectorWhiteningTransformer> | 重みを識別できるように最適化を単純化します。 |

## <a name="row-filters"></a>行フィルター

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowShufflingTransformer> | 指定した行数のプールを使用して、実行しようとしているランダム化されたカーソルをシャッフルします。  |
| <xref:Microsoft.ML.Transforms.SkipFilter> | 行の数をスキップすることで行のサブセットへの入力を制限することができます。 |
| <xref:Microsoft.ML.Transforms.SkipTakeFilter> | 任意のオフセットで行のサブセットへの入力を制限することができます。 データのページングを実装するために使用できます。 SkipTakeFilter.SkipArguments で作成されると、`SkipFilter` として動作します。
| <xref:Microsoft.ML.Transforms.TakeFilter> | 最初の N 行を取得することで行のサブセットへの入力を制限することができます。 |


## <a name="schema"></a>Schema

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnCopyingTransformer> | データセットから列を複製します。|
| <xref:Microsoft.ML.Transforms.ColumnSelectingTransformer> | 特定の入力からドロップまたは保持する列のセットを選択します。 |
| <xref:Microsoft.ML.Transforms.FeatureSelection.SlotsDroppingTransformer> | 列からスロットをドロップします。|
| <xref:Microsoft.ML.Transforms.OptionalColumnTransform> | 指定した型と既定値を使用して、新しい列を作成します。 |
| <xref:Microsoft.ML.Transforms.RangeFilter> | Single、Double または Key (連続) 型の列で dataview をフィルター処理します。 指定した最小/最大の範囲内に値を保持します。 NaNs は常に除外されます。入力が Key 型の場合、最小/最大は値の数の割合と見なされます。 |

## <a name="tensorflow"></a>TensorFlow

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | 事前トレーニング済みの TensorFlow モデルを使用してスコア付けするか、TensorFlow モデルを再トレーニングします。 |

## <a name="text-processing-and-featurization"></a>テキスト処理と特徴付け

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.TextNormalizingTransformer> | テキストの大文字と小文字の正規化、分音記号、句読点、数字を削除できるテキストの正規化変換。 変換は、テキスト入力とトークンまたテキストのベクター (ReadOnlyMemory のベクター) で動作します。 |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | テキストが文字のシーケンスと見なされる文字指向のトークナイザー。 |

## <a name="time-series"></a>時系列

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesProcessing.ExponentialAverageTransform> | 値の加重平均を取得します。ExpAvg(y_t) = a * y_t + (1-a) * ExpAvg(y_(t-1)) |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidChangePointDetector> | アダプティブ カーネル密度の推定とマーチンゲールに基づいて、i.i.d. シーケンス (ランダムなサンプル) の変更点の検出機能変換を実装します。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidSpikeDetector> | アダプティブ カーネル密度の推定に基づいて、i.i.d. シーケンス (ランダムなサンプル) のスパイクの検出機能変換を実装します。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.MovingAverageTransform> | スライディング ウィンドウの値の加重平均を提供します。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.PercentileThresholdTransform> | 時系列の現在の値がスライディング ウィンドウのトップ値パーセンタイルに属しているかどうかを判断します。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.PValueTransform> | スライディング ウィンドウ内の他の値に基づいて、時系列の現在の値の経験的 p 値を計算します。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.SlidingWindowTransform> | Single 型の時系列でスライディング ウィンドウを出力します。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaChangePointDetector> | 時系列の Singular Spectrum モデリングに基づいて変更点の検出機能変換を実装します。 |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaSpikeDetector> | 時系列の Singular Spectrum モデリングに基づいてスパイクの検出機能変換を実装します。 |

## <a name="miscellaneous"></a>その他

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CompositeTransformer> | Composite DataTransform を作成します。 |
| <xref:Microsoft.ML.Transforms.CustomMappingTransformer%602> | 指定した `IDataView` に追加の列を生成します。 行数は変更せずに、ユーザーの関数の適用結果として、入力データのすべての行に表示されます。|
| <xref:Microsoft.ML.Transforms.GenerateNumberTransform> | 生成された数字シーケンスを使用して列を追加します。 |
| <xref:Microsoft.ML.Transforms.ProduceIdTransform> | カーソルの ID を使用して列を生成します。 |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | 乱数を生成します。 |
