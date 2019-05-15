---
title: データ変換
description: ML.NET でサポートされている機能エンジニアリングのコンポーネントについて検証します。
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: d3261f88a8e52c71f8ddf4d3d5c90b2e2b22b620
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64636554"
---
# <a name="data-transformations"></a>データ変換

データ変換は、モデルのトレーニング用データを準備するために使用されます。 このガイドの変換は、[IEstimator](xref:Microsoft.ML.IEstimator`1) インターフェイスを実装するクラスを返します。 データ変換はまとめて連結することができます。 各変換は、リンクされた参照ドキュメントで指定されている特定の種類および形式のデータを想定し、生成します。

一部のデータ変換には、そのパラメーターを計算するためにトレーニング データが必要です。 たとえば、<xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> トランスフォーマーは、`Fit()` の操作中にトレーニング データの平均と分散を計算し、`Transform()` 操作でそのパラメーターを使用します。 

他のデータ変換はトレーニング データを必要としません。 たとえば、<xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> の変換は、`Fit()` の操作中にトレーニング データを確認せずに `Transform()` の操作を実行できます。

## <a name="column-mapping-and-grouping"></a>列のマップとグループ化

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | 1 つ以上の入力列を新しい出力列に連結します |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | 1 つ以上の入力列をコピーして名前を変更します |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | 1 つ以上の入力列をドロップします |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | 入力データから保持する 1 つ以上の列を選択します |

## <a name="normalization-and-scaling"></a>正規化とスケーリング

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | (トレーニング データの) 平均を引き、(トレーニング データの) 分散で割ります |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | トレーニング データの対数に基づいて正規化します |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | 入力ベクターを [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions) でスケーリングします。この p は 1、2、または無限大です。 既定値は l2 (ユークリッド距離) ノルムです |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | 行データの平均を減算して行の各値をスケーリングし、標準偏差または (行データの) l2-norm で除算し、構成可能なスケール係数 (既定値は 2) で乗算します |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | 入力値をビンのインデックスに割り当て、ビンの数で除算して 0 から 1 の間の float 値を生成します。 ビンの境界は、ビン全体にトレーニング データを均等に分散するように計算されます |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | ラベル列との相関関係に基づいて入力値をビンに割り当てます |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | トレーニング データの最小値と最大値の差で入力をスケーリングします |

## <a name="conversions-between-data-types"></a>データ型間の変換

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | 入力列の型を新しい型に変換します |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | 指定されたマッピングのディクショナリに基づいて、値をキー (カテゴリ) にマップします。 |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | 入力データからマッピングを作成して値をキー (カテゴリ) にマップします |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | キーを変換して元の値に戻します |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | キーを変換して元の値のベクターに戻します |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | キーを変換して元の値のバイナリ ベクターに戻します |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | 入力列の値をハッシュします |

## <a name="text-transformations"></a>テキスト変換

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | テキスト列を正規化された ngram と char-gram のカウントの float 配列に変換します | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | 1 つ以上のテキスト列を個々の単語に分割します |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | 1 つ以上のテキスト列を一連のトピックに関する個々の文字 float に分割します |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | 大文字と小文字の変更、分音記号、句読点、および数字の削除 |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | テキスト列を ngram のカウント (連続する単語のシーケンス) バッグに変換します|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | テキスト列を ngram ベクターのバッグに変換します |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | テキスト列をハッシュされた ngram のカウントのベクターに変換します |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | テキスト列をハッシュされた ngram のカウントのバッグに変換します |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | 指定された言語の既定のストップ ワードを入力列から削除します |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | 入力列から指定されたストップ ワードを削除します |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | 一連のトピックにわたって、ドキュメント (float のベクターとして表されます) を float のベクターに変換します |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | レーニング済みのモデルを使用して、テキスト トークンを文のベクターに変換します |

## <a name="image-transformations"></a>画像変換

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | 画像をグレースケールに変換します |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | ピクセルのベクターを <xref:Microsoft.ML.Transforms.Image.ImageDataViewType> に変換します |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | 入力画像のピクセルを数値のベクターに変換します |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | フォルダーの画像をメモリに読み込みます |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | イメージのサイズを変更する |

## <a name="categorical-data-transformations"></a>分類データの変換

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | 1 つ以上のテキスト列を [one-hot](https://en.wikipedia.org/wiki/One-hot) エンコード済みベクターに変換します |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | もう 1 つのテキスト列をハッシュベースの one-hot エンコード済みベクターに変換します |

## <a name="missing-values"></a>欠損値

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | 新しいブール出力列を作成します。入力列の値が欠落している場合、その値は true です。 |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | 新しい出力列を作成します。値が入力列にない場合は値が既定値に設定され、それ以外の場合は入力値が設定されます |

## <a name="feature-selection"></a>フィーチャーの選択

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | 既定以外の値がしきい値より大きい特徴を選択します |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | ラベル列のデータが最も依存している特徴を選択します |

## <a name="custom-transformations"></a>カスタム変換

| 変換 | 定義 |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | ユーザー定義マッピングを使用して既存の列を新しい列に変換します |
