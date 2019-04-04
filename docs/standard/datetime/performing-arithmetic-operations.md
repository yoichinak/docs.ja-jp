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
ms.openlocfilehash: 2d5f807481468b61365c8b4d8412f12a4741ebb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503160"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>日付と時刻を使用した算術演算の実行

両方、<xref:System.DateTime>と<xref:System.DateTimeOffset>構造体の値に対する算術演算を実行するメンバーを提供する、算術演算の結果は非常に異なります。 このトピックでは、それらの相違点を調べ、それらに関連する日付と時刻のデータのタイム ゾーン対応度し、完全な日付と時刻のデータを使用してタイム ゾーン対応した操作を実行する方法について説明します。

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>比較と DateTime 値を使用した算術演算

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティにより、<xref:System.DateTimeKind>に日付と時刻を現地時刻、世界協定時刻 (UTC)、または未指定のタイム ゾーンの時刻を表すかどうかを示すために割り当てられる値。 ただし、比較または日付と時刻の演算を実行するときにこの制限付きのタイム ゾーン情報が無視<xref:System.DateTimeKind>値。 次の例では、現在の現地時刻と現在の UTC 時刻を比較することで、この問題を示しています。

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29>メソッドによって報告されるローカル時刻より前 (またはより小さい)、UTC 時刻と減算演算を示します米国で UTC と、システムのローカル時刻の違い7 時間であることを示しています。 しかし、これら 2 つの値は、ある特定の時点を異なる表現で示したものであるため、この場合、時間差の原因は、UTC を基準としたローカル タイム ゾーンのオフセットにあることは明らかです。

一般的には、<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティによって返される結果は影響しません<xref:System.DateTime.Kind>比較および算術メソッド (2 つ同じ時点の比較を示します) と、その結果の解釈の影響を与えることができます。 例:

* 算術演算の結果を持つ 2 つの日付と時刻の値で実行<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティが両方とも<xref:System.DateTimeKind>2 つの値の間の実際の時間間隔を反映します。 同様に、そのような 2 つの日付と時刻の値を比較した結果には、2 つの時間の関係が正確に反映されます。

* 算術演算または比較操作の結果が持つ 2 つの日付と時刻の値に対して実行<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティが両方とも<xref:System.DateTimeKind>または 2 つの日付と時刻値が異なる<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティの値が時刻の差が反映されます2 つの値。

* ローカルの日付と時刻の値に対する算術演算または比較操作では、特定の値があいまいであるかや、無効であるかどうかは考慮されず、ローカル タイム ゾーンでの夏時間の開始や終了による調整規則の影響についても考慮されません。

* UTC と現地時刻の差を比較または計算する操作の結果には、UTC を基準としたローカル タイム ゾーンのオフセットに等しい時間差が含まれます。

* タイム ゾーンが指定されていない時刻と UTC または現地時刻との差を比較または計算する操作では、単純な時刻差が反映されます。 タイム ゾーンの違いは考慮されず、結果にはタイム ゾーン調整規則の適用が反映されません。

* タイム ゾーンが指定されていない 2 つの時刻の差を比較または計算する操作の結果には、2 つの異なるタイム ゾーンの時刻の差を反映した未知の時間差が含まれる場合があります。

多くのシナリオでは、あるタイム ゾーンの相違点には影響しません日付と時刻の計算 (これらのいくつかの詳細については、次を参照してください[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](../../../docs/standard/datetime/choosing-between-datetime.md)) にコンテキスト。日付と時刻のデータは、比較演算子または算術演算の意味を定義します。

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>比較と DateTimeOffset 値を使用した算術演算

A<xref:System.DateTimeOffset>値には、日付と時刻だけでなくを明確に定義されたその日付と時刻が UTC を基準としてオフセットが含まれています。 いくらか異なる等価性を定義できるようになります<xref:System.DateTimeOffset>値。 一方<xref:System.DateTime>値が同じ日付と時刻の値がある場合は、等しい<xref:System.DateTimeOffset>値が時間で同じポイントを参照している場合は等しい。 これにより、<xref:System.DateTimeOffset>値より正確なとの比較と 2 つの日付と時刻の間隔を決定するほとんどの算術演算で使用する際の解釈が必要な少なくします。 次の例では、 <xref:System.DateTimeOffset> UTC とローカルと比較した前の例に相当<xref:System.DateTimeOffset>値は、この動作の違いを示しています。

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

この例で、<xref:System.DateTimeOffset.CompareTo%2A>メソッドは、現在の現地時刻と現在の UTC 時刻が等しく、減算のことを示します<xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)>値では、2 つの時刻の差があることを示します<xref:System.TimeSpan.Zero?displayProperty=nameWithType>します。

最高の使用制限<xref:System.DateTimeOffset>が日付と時刻の演算の値は<xref:System.DateTimeOffset>値があるいくつかのタイム ゾーンの処理が、これらは完全にタイム ゾーンに注意してください。 ですが、<xref:System.DateTimeOffset>値のオフセット UTC からタイム ゾーンのオフセットを反映するときに、<xref:System.DateTimeOffset>最初、変数に値が割り当てられる、その後、タイム ゾーンから解除になります。 特定可能な時刻との直接の関連付けは失われるため、日付と時刻の間隔に対して加算や減算を行っても、タイム ゾーンの調整規則は考慮されません。

たとえば、米国の中部標準時のタイム ゾーンが夏時間に移行するのは、 2008 年 3 月 9 日の午前 2 時です。 つまり、中部標準時の 2008 年 3 月 9 日の午前 1 時 30 分に 2 時間 30 分の間隔を加算すると、日付と時刻は 2008 年 3 月 9 日の 午前 5 時になります。 しかし、次の例に示すように、加算の結果は 2008 年 3 月 9 日の 午前 4 時です。 この操作の結果は正しい時点を表していますが、目的のタイム ゾーンの時刻ではありません (つまり、予想されるタイム ゾーンのオフセットが適用されていません)。

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>タイム ゾーンの時刻を使用した算術演算

<xref:System.TimeZoneInfo>クラスには数から 1 つのタイム ゾーンで時間を変換するときに、調整を自動的に適用される変換メソッドが含まれています。 次に例を示します。

* <xref:System.TimeZoneInfo.ConvertTime%2A>と<xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>メソッドで、任意の 2 つのタイム ゾーン間での時刻に変換します。

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>と<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>メソッドは、特定のタイム ゾーンの時刻 (UTC) を変換または特定のタイム ゾーンの時刻を UTC に変換します。

詳細については、[タイム ゾーン間で時刻の変換](../../../docs/standard/datetime/converting-between-time-zones.md)を参照してください。

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)>クラスは、日付と時刻の演算を実行するときに、調整規則を自動的に適用されるすべてのメソッドを提供しません。 ただし、あるタイム ゾーンの時刻を UTC に変換してから算術演算を実行し、その後 UTC から元のタイム ゾーンの時刻に再変換することで、調整規則を適用したときと同じ結果を得ることができます。 詳細については、次を参照してください。[方法。日付と時刻の演算でタイム ゾーンを使用して](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)します。

たとえば、次のコードは、2008 年 3 月 9 日の午前 2 時に 2 時間 30 分を加算する 前のコードと似ています。 ただし、中部標準時を UTC に変換した後に日付と時刻の算術演算を実行し、その結果を UTC から中部標準時に変換するため、得られた時刻は中部標準時タイム ゾーンの夏時間への移行を反映しています。

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [方法: 日付と時刻の演算でタイム ゾーンを使用します。](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
