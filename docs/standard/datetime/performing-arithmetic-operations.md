---
title: 日付と時刻を使用した算術演算の実行
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
ms.openlocfilehash: 0db0331620da8337930bfacf5d1bbd9913647afa
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344169"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>日付と時刻を使用した算術演算の実行

<xref:System.DateTime>構造体と構造体の両方<xref:System.DateTimeOffset>が、その値に対して算術演算を実行するメンバーを提供しますが、算術演算の結果は大きく異なります。 このトピックでは、これらの相違点を調べ、日付と時刻のデータでタイム ゾーン認識の度合いに関連付け、日付と時刻のデータを使用して完全なタイム ゾーン対応操作を実行する方法について説明します。

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>DateTime 値を使用した比較と算術演算

この<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティを使用<xref:System.DateTimeKind>すると、日付と時刻に値を割り当てることによって、その値がローカル時刻、世界協定時刻 (UTC)、または指定されていないタイム ゾーンの時刻のいずれを表すかを示すことができます。 ただし、この制限されたタイム ゾーン情報は、値を<xref:System.DateTimeKind>比較または実行するときに無視されます。 次の例では、現在の現地時刻と現在の UTC 時刻を比較することで、この問題を示しています。

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

この<xref:System.DateTime.CompareTo%28System.DateTime%29>メソッドは、ローカル時刻が UTC 時刻より前 (またはより小さい) と報告し、減算操作は、UTC と米国太平洋標準時ゾーンのシステムのローカル時間の差が 7 時間であることを示します。 ただし、これら 2 つの値は 1 つの時点の異なる表現を提供するため、この場合、時間間隔が UTC からのローカル タイム ゾーンのオフセットに完全に起因していることは明らかです。

より一般的には<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>、このプロパティは比較および算術メソッド<xref:System.DateTime.Kind>によって返される結果には影響しません (2 つの同一の時点の比較が示すように) これらの結果の解釈に影響を与える可能性があります。 次に例を示します。

- 2 つの日付と時刻の値に対して実行された算術<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>演算の結果<xref:System.DateTimeKind>は、プロパティが両方とも等しい場合に、2 つの値の実際の時間間隔を反映します。 同様に、そのような 2 つの日付と時刻の値を比較した結果には、2 つの時間の関係が正確に反映されます。

- プロパティが等しい<xref:System.DateTime.Kind%2A?displayProperty=nameWithType><xref:System.DateTimeKind>か、プロパティ値が異なる<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>2 つの日付と時刻の値の両方で実行される算術演算または比較演算の結果は、2 つの値のクロック時間の差を反映します。

- ローカルの日付と時刻の値に対する算術演算または比較操作では、特定の値があいまいであるかや、無効であるかどうかは考慮されず、ローカル タイム ゾーンでの夏時間の開始や終了による調整規則の影響についても考慮されません。

- UTC と現地時刻の差を比較または計算する操作の結果には、UTC を基準としたローカル タイム ゾーンのオフセットに等しい時間差が含まれます。

- タイム ゾーンが指定されていない時刻と UTC または現地時刻との差を比較または計算する操作では、単純な時刻差が反映されます。 タイム ゾーンの違いは考慮されず、結果にはタイム ゾーン調整規則の適用が反映されません。

- タイム ゾーンが指定されていない 2 つの時刻の差を比較または計算する操作の結果には、2 つの異なるタイム ゾーンの時刻の差を反映した未知の時間差が含まれる場合があります。

タイム ゾーンの違いが日付と時刻の計算に影響を与えないシナリオが多数あります (これらの一部については[、「DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の選択](../../../docs/standard/datetime/choosing-between-datetime.md)」を参照してください)。

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>日付時刻オフセット値を使用した比較および算術演算

値<xref:System.DateTimeOffset>には、日付と時刻だけでなく、UTC に対するその日付と時刻を明確に定義するオフセットも含まれます。 これにより、値とは多少異なる等価性を<xref:System.DateTimeOffset>定義することが可能になります。 値<xref:System.DateTime>が同じ日時値を持つ場合は等しくなりますが<xref:System.DateTimeOffset>、両方が同じ時点を参照する場合は値は等しくなります。 これにより、比較<xref:System.DateTimeOffset>や、2 つの日時の間隔を決定するほとんどの算術演算で使用する場合、値の精度が高まり、解釈の必要性が少なくなります。 次の例は、ローカル値<xref:System.DateTimeOffset>と UTC<xref:System.DateTimeOffset>値を比較した前の例と同等であり、この動作の違いを示しています。

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

この例では、メソッド<xref:System.DateTimeOffset.CompareTo%2A>は現在のローカル時刻と現在の UTC 時刻が等しいことを示し、値<xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)>の減算は 2 つの時間の<xref:System.TimeSpan.Zero?displayProperty=nameWithType>差が .

日付と時刻の算術<xref:System.DateTimeOffset>計算で値を使用する主な制限<xref:System.DateTimeOffset>は、値にはいくつかのタイム ゾーン認識がありますが、タイム ゾーンを完全に認識しないことです。 値の<xref:System.DateTimeOffset>オフセットは<xref:System.DateTimeOffset>、変数に最初に値が割り当てられたときに UTC からのタイム ゾーンのオフセットを反映しますが、その後はタイム ゾーンとの関連付けが解除されます。 特定可能な時刻との直接の関連付けは失われるため、日付と時刻の間隔に対して加算や減算を行っても、タイム ゾーンの調整規則は考慮されません。

例として、米国中部標準時ゾーンの夏時間への移行は午前 2 時に行われます。 発生します。 つまり、中部標準時の 2008 年 3 月 9 日の午前 1 時 30 分に 2 時間 30 分の間隔を加算すると、日付と時刻は 2008 年 3 月 9 日の 発生します。 しかし、次の例に示すように、加算の結果は 2008 年 3 月 9 日の 発生します。 この操作の結果は、正しい時点を表しますが、対象となるタイム ゾーンの時刻ではありません (つまり、予想されるタイム ゾーン オフセットがありません)。

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>タイム ゾーン内の時間を含む算術演算

この<xref:System.TimeZoneInfo>クラスには、タイム ゾーン間で時刻を変換するときに自動的に調整を適用する変換メソッドが多数含まれています。 コーディネートは次のとおりです。

- <xref:System.TimeZoneInfo.ConvertTime%2A>と<xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>メソッドは、任意の 2 つのタイム ゾーン間の時刻を変換します。

- <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>と<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>メソッドは、特定のタイム ゾーンの時刻を UTC に変換するか、UTC を特定のタイム ゾーンの時刻に変換します。

詳細については、[タイム ゾーン間の時刻の変換を](../../../docs/standard/datetime/converting-between-time-zones.md)参照してください。

この<xref:System.TimeZoneInfo>クラスには、日付と時刻の算術演算を実行するときに自動的に調整規則を適用するメソッドは用意されていません。 ただし、あるタイム ゾーンの時刻を UTC に変換してから算術演算を実行し、その後 UTC から元のタイム ゾーンの時刻に再変換することで、調整規則を適用したときと同じ結果を得ることができます。 詳細については、「[方法 : 日付と時刻の算術でタイム ゾーンを使用](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)する 」を参照してください。

たとえば、次のコードは、2008 年 3 月 9 日の午前 2 時に 2 時間 30 分を加算する 発生します。 ただし、中部標準時を UTC に変換した後に日付と時刻の算術演算を実行し、その結果を UTC から中部標準時に変換するため、得られた時刻は中部標準時タイム ゾーンの夏時間への移行を反映しています。

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [方法: 日付と時刻の演算でタイム ゾーンを使用する](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
