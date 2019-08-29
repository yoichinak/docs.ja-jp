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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01314c160fc531f5c97a1369c8444dce7f590d53
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106610"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>日付と時刻を使用した算術演算の実行

<xref:System.DateTime> との構造体はどちらも、値に対して算術演算を実行するメンバーを提供しますが、算術演算の結果は<xref:System.DateTimeOffset>大きく異なります。 このトピックでは、これらの相違点を確認し、日付と時刻のデータのタイムゾーン認識の程度に関連付けて、日付と時刻のデータを使用して完全なタイムゾーン対応操作を実行する方法について説明します。

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>DateTime 値を使用した比較と算術演算

プロパティを使用すると、日付と時刻に値を割り当てて、現地時刻、世界協定時刻(UTC)、または指定されていないタイムゾーンの時刻を表すかどうかを示すことができます。<xref:System.DateTimeKind> <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> ただし、この限られたタイムゾーン情報は、値に対して日付と時刻<xref:System.DateTimeKind>の演算を比較または実行するときには無視されます。 次の例では、現在の現地時刻と現在の UTC 時刻を比較することで、この問題を示しています。

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

メソッド<xref:System.DateTime.CompareTo%28System.DateTime%29>は、現地時刻が utc 時刻よりも前 (またはそれ未満) であることを報告します。減算演算は、utc と米国のシステムの現地時刻との差を示します。7 時間であることを示しています。 しかし、これら 2 つの値は、ある特定の時点を異なる表現で示したものであるため、この場合、時間差の原因は、UTC を基準としたローカル タイム ゾーンのオフセットにあることは明らかです。

一般に、プロパティ<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>は、比較および算術メソッドによっ<xref:System.DateTime.Kind>て返される結果には影響しません (2 つの同じ時点の比較が示すため)。ただし、これらの結果の解釈に影響する可能性があります。 例:

- <xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティが両方とも等しい<xref:System.DateTimeKind> 2 つの日付と時刻の値に対して実行される算術演算の結果は、2つの値の間の実際の時間間隔を反映します。 同様に、そのような 2 つの日付と時刻の値を比較した結果には、2 つの時間の関係が正確に反映されます。

- 2つの日付と時刻<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> <xref:System.DateTimeKind>の値が異なる<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティ値を持つ2つの日付と時刻の値に対して実行される算術演算または比較演算の結果は、クロック時間の差を反映します。2つの値の間。

- ローカルの日付と時刻の値に対する算術演算または比較操作では、特定の値があいまいであるかや、無効であるかどうかは考慮されず、ローカル タイム ゾーンでの夏時間の開始や終了による調整規則の影響についても考慮されません。

- UTC と現地時刻の差を比較または計算する操作の結果には、UTC を基準としたローカル タイム ゾーンのオフセットに等しい時間差が含まれます。

- タイム ゾーンが指定されていない時刻と UTC または現地時刻との差を比較または計算する操作では、単純な時刻差が反映されます。 タイム ゾーンの違いは考慮されず、結果にはタイム ゾーン調整規則の適用が反映されません。

- タイム ゾーンが指定されていない 2 つの時刻の差を比較または計算する操作の結果には、2 つの異なるタイム ゾーンの時刻の差を反映した未知の時間差が含まれる場合があります。

タイムゾーンの違いが日付と時刻の計算に影響しないシナリオは多数あります (これらのいくつかの詳細については、「 [DateTime、DateTimeOffset、TimeSpan、TimeZoneInfo の選択](../../../docs/standard/datetime/choosing-between-datetime.md)」を参照してください)。または日付と時刻のデータのコンテキストについても説明します。比較または算術演算の意味を定義します。

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>DateTimeOffset 値を使用した比較と算術演算

値<xref:System.DateTimeOffset>には、日付と時刻だけでなく、UTC を基準とする日付と時刻を明確に定義するオフセットも含まれます。 これにより、値の場合とは異なる方法<xref:System.DateTimeOffset>で等しいかどうかを定義できます。 一方<xref:System.DateTime> 、値は同じ日付と時刻の値を持つ場合は<xref:System.DateTimeOffset>等しいのに対し、両方とも同じ時点を参照している場合、値は等しいと見なされます。 これにより<xref:System.DateTimeOffset> 、比較で使用する場合の解釈や、2つの日付と時刻の間隔を決定するほとんどの算術演算において、値の精度が向上し、解釈が不要になります。 次の例は、ローカル値<xref:System.DateTimeOffset>と UTC <xref:System.DateTimeOffset>値を比較した前の例と同等のものであり、動作の違いを示しています。

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

この例では、 <xref:System.DateTimeOffset.CompareTo%2A>メソッドは現在の現地時刻と現在の UTC 時刻が等しいことを示し、値<xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)>の減算は2つの時刻の差が<xref:System.TimeSpan.Zero?displayProperty=nameWithType>であることを示しています。

日付と時刻の演算<xref:System.DateTimeOffset>で値を使用する場合の上限は<xref:System.DateTimeOffset> 、値がタイムゾーンに対応しているにもかかわらず、タイムゾーンを完全に認識していないことです。 値の<xref:System.DateTimeOffset>オフセットには、変数に<xref:System.DateTimeOffset>最初に値が割り当てられたときの UTC からのタイムゾーンのオフセットが反映されますが、それ以降はタイムゾーンとの関連付けが解除されます。 特定可能な時刻との直接の関連付けは失われるため、日付と時刻の間隔に対して加算や減算を行っても、タイム ゾーンの調整規則は考慮されません。

たとえば、米国の中部標準時のタイム ゾーンが夏時間に移行するのは、 2008 年 3 月 9 日の午前 2 時です。 つまり、中部標準時の 2008 年 3 月 9 日の午前 1 時 30 分に 2 時間 30 分の間隔を加算すると、日付と時刻は 2008 年 3 月 9 日の 午前 5 時になります。 しかし、次の例に示すように、加算の結果は 2008 年 3 月 9 日の 午前 4 時です。 この操作の結果は正しい時点を表していますが、目的のタイム ゾーンの時刻ではありません (つまり、予想されるタイム ゾーンのオフセットが適用されていません)。

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>タイムゾーンの時刻を使用した算術演算

クラス<xref:System.TimeZoneInfo>には、あるタイムゾーンから別のタイムゾーンに時刻を変換するときに調整を自動的に適用する多くの変換メソッドが含まれています。 次に例を示します。

- メソッド<xref:System.TimeZoneInfo.ConvertTime%2A> と<xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>メソッド。2つのタイムゾーン間で時刻を変換します。

- メソッド<xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> と<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>メソッド。特定のタイムゾーンの時刻を utc に変換するか、utc を特定のタイムゾーンの時刻に変換します。

詳細については、「[タイムゾーン間での時刻の変換](../../../docs/standard/datetime/converting-between-time-zones.md)」を参照してください。

クラス<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)>には、日付と時刻の演算を実行するときに調整規則を自動的に適用するメソッドは用意されていません。 ただし、あるタイム ゾーンの時刻を UTC に変換してから算術演算を実行し、その後 UTC から元のタイム ゾーンの時刻に再変換することで、調整規則を適用したときと同じ結果を得ることができます。 詳細については、「[方法: 日付と時刻の演算](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)でタイムゾーンを使用します。

たとえば、次のコードは、2008 年 3 月 9 日の午前 2 時に 2 時間 30 分を加算する 前のコードと似ています。 ただし、中部標準時を UTC に変換した後に日付と時刻の算術演算を実行し、その結果を UTC から中部標準時に変換するため、得られた時刻は中部標準時タイム ゾーンの夏時間への移行を反映しています。

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [方法: 日付と時刻の演算でタイムゾーンを使用する](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
