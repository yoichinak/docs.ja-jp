---
title: DateTime と DateTimeOffset 間の変換
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb91ed8edd0c5cd3cb1d051157596f311718195d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107061"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>DateTime と DateTimeOffset 間の変換

構造体<xref:System.DateTimeOffset>は、 <xref:System.DateTime>構造体よりも高い範囲のタイムゾーンを認識<xref:System.DateTime>しますが、メソッドの呼び出しでは、より一般的にパラメーターが使用されます。 このため、値を値に<xref:System.DateTimeOffset> <xref:System.DateTime>変換したり、その逆の変換を行ったりすることは、特に重要です。 このトピックでは、できるだけ多くのタイムゾーン情報を保持する方法でこれらの変換を実行する方法について説明します。

> [!NOTE]
> との両方の型には、タイムゾーンの時刻を表すときにいくつかの制限があります。 <xref:System.DateTimeOffset> <xref:System.DateTime> プロパティを使用する<xref:System.DateTime>と、は世界協定時刻 (UTC) とシステムのローカルタイムゾーンのみを反映できます。 <xref:System.DateTime.Kind%2A> <xref:System.DateTimeOffset>UTC からの時刻のオフセットを反映しますが、そのオフセットが属する実際のタイムゾーンは反映されません。 時刻の値とタイムゾーンのサポートの詳細については、「 [DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](../../../docs/standard/datetime/choosing-between-datetime.md)」を参照してください。

## <a name="conversions-from-datetime-to-datetimeoffset"></a>DateTime から DateTimeOffset への変換

この<xref:System.DateTimeOffset>構造体は、ほとんどの変換<xref:System.DateTime>に<xref:System.DateTimeOffset>適した変換に対して実行する2つの同等の方法を提供します。

- コンストラクター。 <xref:System.DateTime>値に基づいて新しい<xref:System.DateTimeOffset>オブジェクトを作成します。 <xref:System.DateTimeOffset.%23ctor%2A>

- 暗黙的な変換演算子。これにより、 <xref:System.DateTime> <xref:System.DateTimeOffset>オブジェクトに値を割り当てることができます。

Utc 値とローカル<xref:System.DateTime>値の場合<xref:System.DateTimeOffset.Offset%2A> 、結果<xref:System.DateTimeOffset>の値のプロパティに utc またはローカルタイムゾーンオフセットが正確に反映されます。 たとえば、次のコードは、UTC 時刻をそれと等価<xref:System.DateTimeOffset>な値に変換します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

この場合、`utcTime2` 変数のオフセットは 00:00 です。 同様に、次のコードは、現地時刻をそれ<xref:System.DateTimeOffset>と等価な値に変換します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

ただし、 <xref:System.DateTime.Kind%2A>プロパティ<xref:System.DateTime>が<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>である値の場合、これら2つの<xref:System.DateTimeOffset>変換メソッドは、オフセットがローカルタイムゾーンの値である値を生成します。 米国の太平洋標準時ゾーンでの実行例を次に示します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

値にローカルタイムゾーンまたは UTC 以外の日付と時刻が反映されている場合は、オーバーロード<xref:System.DateTimeOffset.%23ctor%2A>され<xref:System.DateTimeOffset>たコンストラクターを呼び出すことによって、値を値に変換し、そのタイムゾーン情報を保持することができます。 <xref:System.DateTime> たとえば、次の例では、 <xref:System.DateTimeOffset>中部標準時を反映するオブジェクトをインスタンス化しています。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

このコンストラクターのオーバーロード<xref:System.TimeSpan>に対する2番目のパラメーターは、時刻の UTC からのオフセットを表すオブジェクトで、時刻に対応するタイムゾーンの<xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType>メソッドを呼び出すことによって取得する必要があります。 メソッドの1つのパラメーターは<xref:System.DateTime> 、変換する日付と時刻を表す値です。 タイム ゾーンで夏時間がサポートされている場合、このパラメーターにより、このメソッドはその特定の日時に対して適切なオフセットを決定できます。

## <a name="conversions-from-datetimeoffset-to-datetime"></a>DateTimeOffset から DateTime への変換

プロパティ<xref:System.DateTimeOffset.DateTime%2A>は、変換を<xref:System.DateTime>実行<xref:System.DateTimeOffset>するために最も一般的に使用されます。 ただし、次の例<xref:System.DateTime>に示す<xref:System.DateTime.Kind%2A>ように<xref:System.DateTimeKind.Unspecified>、このメソッドは、プロパティがである値を返します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

これは、 <xref:System.DateTimeOffset.DateTime%2A>プロパティを使用する<xref:System.DateTimeOffset>ときに、値と UTC の関係に関する情報が変換によって失われることを意味します。 これは<xref:System.DateTimeOffset> 、UTC 時刻またはシステムの現地時刻に対応する値に影響<xref:System.DateTimeOffset.DateTime%2A>します。これは、構造体が<xref:System.DateTime.Kind%2A>そのプロパティ内の2つのタイムゾーンのみを反映しているためです。

を<xref:System.DateTimeOffset> 値<xref:System.DateTime>に変換するときに、できるだけ多くのタイムゾーン情報を保持するには、 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>プロパティ<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>とプロパティを使用します。

### <a name="converting-a-utc-time"></a>UTC 時刻の変換

変換<xref:System.DateTimeOffset.DateTime%2A>された値が UTC 時刻であることを示すには、 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>プロパティの値を取得します。 これは、次<xref:System.DateTimeOffset.DateTime%2A>の2つの方法でプロパティとは異なります。

- このメソッドは<xref:System.DateTime> 、 <xref:System.DateTime.Kind%2A>プロパティがで<xref:System.DateTimeKind.Utc>ある値を返します。

- プロパティ値がと等しく<xref:System.TimeSpan.Zero?displayProperty=nameWithType>ない場合は、時刻を UTC に変換します。 <xref:System.DateTimeOffset.Offset%2A>

> [!NOTE]
> 変換<xref:System.DateTime>された値が明確に単一の時点を識別するようにアプリケーションで要求さ<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>れる場合は、 <xref:System.DateTimeOffset>プロパティを使用してすべての変換を<xref:System.DateTime>処理することを検討してください。

次のコードでは<xref:System.DateTimeOffset.UtcDateTime%2A> 、プロパティを使用して、オフセット<xref:System.TimeSpan.Zero?displayProperty=nameWithType>がに<xref:System.DateTime>等しい<xref:System.DateTimeOffset>値を値に変換します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

次のコードでは<xref:System.DateTimeOffset.UtcDateTime%2A> 、プロパティを使用して、 <xref:System.DateTimeOffset>値に対してタイムゾーン変換と型変換の両方を実行します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>現地時刻の変換

<xref:System.DateTimeOffset>値が現地時刻を表すことを示すには、 `static` <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType>プロパティに<xref:System.DateTime>よって返された値を (`Shared` Visual Basic) <xref:System.DateTime.SpecifyKind%2A>メソッドに渡すことができます。 メソッドは、最初のパラメーターとして渡された日付と時刻を返します<xref:System.DateTime.Kind%2A>が、プロパティは、2番目のパラメーターで指定した値に設定されます。 次のコードでは<xref:System.DateTime.SpecifyKind%2A> 、オフセットがローカル<xref:System.DateTimeOffset>タイムゾーンのオフセットに対応する値を変換するときに、メソッドを使用しています。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

また、プロパティを使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>して、 <xref:System.DateTimeOffset>値をローカル<xref:System.DateTime>値に変換することもできます。 <xref:System.DateTimeKind.Local>戻り<xref:System.DateTime.Kind%2A> 値の<xref:System.DateTime>プロパティがです。 次のコードでは<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> 、オフセットがローカル<xref:System.DateTimeOffset>タイムゾーンのオフセットに対応する値を変換するときに、プロパティを使用しています。 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

<xref:System.DateTime> `get` <xref:System.DateTimeOffset> <xref:System.DateTimeOffset.ToLocalTime%2A>プロパティを使用して値を取得すると、プロパティのアクセサーは、最初に値を UTC に変換してから、メソッドを呼び出して現地時刻に変換します。 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> これは、 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>プロパティから値を取得して、型変換を実行するときと同時にタイムゾーン変換を実行できることを意味します。 また、変換の実行にローカル タイム ゾーンの調整規則が適用されることも意味します。 次のコードは、 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>プロパティを使用して、型とタイムゾーン変換の両方を実行する方法を示しています。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>汎用変換メソッド

次の例では、値`ConvertFromDateTimeOffset`を値<xref:System.DateTimeOffset>に<xref:System.DateTime>変換するという名前のメソッドを定義しています。 オフセットに基づいて、 <xref:System.DateTimeOffset>値が UTC 時刻、現地時刻、またはその他の時刻であるかどうかを判断し、返された日付と時刻の値の<xref:System.DateTime.Kind%2A>プロパティをそれに応じて定義します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

次の例では`ConvertFromDateTimeOffset` 、メソッド<xref:System.DateTimeOffset>を呼び出して、UTC 時刻、現地時刻、および米国の時刻を表す値を変換します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

このコードは次の 2 つのことを前提としますが、アプリケーションおよびその日時値のソースによっては常に有効とは限らないことに注意してください。

- オフセットが<xref:System.TimeSpan.Zero?displayProperty=nameWithType> UTC を表す日付と時刻の値であることを前提としています。 実際には、UTC は特定のタイム ゾーンの時刻ではなく、世界のタイム ゾーンの時刻を標準化する際に基準となる時刻です。 タイムゾーンには、の<xref:System.TimeSpan.Zero>オフセットを設定することもできます。

- オフセットがローカル タイム ゾーンのオフセットと等しい日時が、ローカル タイム ゾーンを表すことを前提とします。 日時値は元のタイム ゾーンとの関連付けが解除されているので、これは該当しない場合があります。日時は、同じオフセットを持つ別のタイム ゾーンに由来する可能性があります。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
