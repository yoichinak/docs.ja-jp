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
ms.openlocfilehash: d4bce84d26e8f498f065c887b583e18d8ea7c786
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61901928"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>DateTime と DateTimeOffset 間の変換

ですが、<xref:System.DateTimeOffset>構造体は、タイム ゾーンの処理よりも高い、<xref:System.DateTime>構造、<xref:System.DateTime>パラメーターがメソッドの呼び出しでよく使用されます。 このため、変換する機能<xref:System.DateTimeOffset>値<xref:System.DateTime>値し、その逆の場合は特に重要です。 このトピックでは、できるだけ多くのタイム ゾーン情報を保持するようにこれらの変換を実行する方法を示します。

> [!NOTE]
> 両方の<xref:System.DateTime>と<xref:System.DateTimeOffset>型タイム ゾーンの時刻を表す場合に制限事項があります。 その<xref:System.DateTime.Kind%2A>プロパティ、<xref:System.DateTime>は世界協定時刻 (UTC) と、システムのローカル タイム ゾーンのみを反映するようにできます。 <xref:System.DateTimeOffset> UTC からの時刻のオフセットが、実際のタイム ゾーン オフセットが属するは反映されませんが反映されます。 詳細については、時刻の値とタイム ゾーンのサポートは、次を参照してください。[選択の間で DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)します。

## <a name="conversions-from-datetime-to-datetimeoffset"></a>DateTime から DateTimeOffset への変換

<xref:System.DateTimeOffset>構造体を実行する 2 つの同等の方法を提供します。<xref:System.DateTime>に<xref:System.DateTimeOffset>、ほとんどの変換に適した変換。

* <xref:System.DateTimeOffset.%23ctor%2A>コンス トラクターは、新たに作成<xref:System.DateTimeOffset>オブジェクトに基づいて、<xref:System.DateTime>値。

* 暗黙的な変換演算子は、割り当てることができます、<xref:System.DateTime>値を<xref:System.DateTimeOffset>オブジェクト。

UTC と現地<xref:System.DateTime>値、<xref:System.DateTimeOffset.Offset%2A>結果のプロパティ<xref:System.DateTimeOffset>UTC またはローカル タイム ゾーン オフセットを正確に反映します。 たとえば、次のコードを等価の UTC 時刻を変換します.<xref:System.DateTimeOffset>値。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

この場合、`utcTime2` 変数のオフセットは 00:00 です。 次のコードが、現地時刻をそれと同等に変換する同様に、<xref:System.DateTimeOffset>値。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

ただし、<xref:System.DateTime>値を持つ<xref:System.DateTime.Kind%2A>プロパティは<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>、これらの 2 つの変換メソッドの生成、<xref:System.DateTimeOffset>オフセットがローカル タイム ゾーンの値。 米国の太平洋標準時ゾーンでの実行例を次に示します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

場合、<xref:System.DateTime>値が日付とローカル タイム ゾーンまたは UTC 以外に何かの時刻を反映して、変換できる、<xref:System.DateTimeOffset>値し、そのタイム ゾーン情報を保持する、オーバー ロードを呼び出して<xref:System.DateTimeOffset.%23ctor%2A>コンス トラクター。 たとえば、次の例をインスタンス化、<xref:System.DateTimeOffset>中部標準時を反映するオブジェクト。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

このコンス トラクターのオーバー ロードの 2 番目のパラメーターを<xref:System.TimeSpan>を呼び出して UTC からの時刻のオフセットを表すオブジェクトを取得する必要があります、<xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType>時刻の対応するタイム ゾーンのメソッド。 メソッドの 1 つのパラメーターは、<xref:System.DateTime>変換する日付と時刻を表す値です。 タイム ゾーンで夏時間がサポートされている場合、このパラメーターにより、このメソッドはその特定の日時に対して適切なオフセットを決定できます。

## <a name="conversions-from-datetimeoffset-to-datetime"></a>DateTimeOffset から DateTime への変換

<xref:System.DateTimeOffset.DateTime%2A>プロパティを実行する最もよく使用<xref:System.DateTimeOffset>に<xref:System.DateTime>変換します。 ただし、それを返します、<xref:System.DateTime>値<xref:System.DateTime.Kind%2A>プロパティが<xref:System.DateTimeKind.Unspecified>、次の例に示すようにします。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

つまり、すべての情報について、<xref:System.DateTimeOffset>を UTC 値のリレーションシップが、変換によって失われるときに、<xref:System.DateTimeOffset.DateTime%2A>プロパティを使用します。 これは、影響<xref:System.DateTimeOffset>またはシステムのローカル時刻を UTC 時刻に対応しているため、値、<xref:System.DateTimeOffset.DateTime%2A>構造体が 2 つのタイム ゾーンのみを反映してその<xref:System.DateTime.Kind%2A>プロパティ。

変換するときに、できるだけ多くのタイム ゾーン情報を保持するために、<xref:System.DateTimeOffset>を<xref:System.DateTime>使用する値を<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>と<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>プロパティ。

### <a name="converting-a-utc-time"></a>UTC 時刻の変換

いることを示す、変換された<xref:System.DateTimeOffset.DateTime%2A>値が UTC 時刻の値を取得することができます、<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>プロパティ。 異なり、 <xref:System.DateTimeOffset.DateTime%2A> 2 つの方法でのプロパティ。

* 返します、<xref:System.DateTime>値<xref:System.DateTime.Kind%2A>プロパティは<xref:System.DateTimeKind.Utc>します。

* 場合、<xref:System.DateTimeOffset.Offset%2A>プロパティの値が等しくない<xref:System.TimeSpan.Zero?displayProperty=nameWithType>時刻を UTC に変換します。

> [!NOTE]
> アプリケーションでは、変換が必要な場合<xref:System.DateTime>値は明確に単一時点を識別、使用を検討する必要があります、<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>プロパティをすべて処理<xref:System.DateTimeOffset>に<xref:System.DateTime>変換します。

次のコードでは、<xref:System.DateTimeOffset.UtcDateTime%2A>に変換するプロパティを<xref:System.DateTimeOffset>オフセットに等しい値<xref:System.TimeSpan.Zero?displayProperty=nameWithType>を<xref:System.DateTime>値。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

次のコードでは、<xref:System.DateTimeOffset.UtcDateTime%2A>でタイム ゾーン変換と型変換の両方を実行するプロパティを<xref:System.DateTimeOffset>値。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>ローカル時刻の変換

いることを示す、<xref:System.DateTimeOffset>値が現地時刻を表す、渡すことができます、<xref:System.DateTime>によって返される値、<xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType>プロパティを`static`(`Shared` Visual Basic で)<xref:System.DateTime.SpecifyKind%2A>メソッド。 メソッドは、最初のパラメーターとして渡された日時を返しますが、設定、<xref:System.DateTime.Kind%2A>プロパティを 2 番目のパラメーターで指定された値にします。 次のコードでは、<xref:System.DateTime.SpecifyKind%2A>メソッドに変換するときに、<xref:System.DateTimeOffset>オフセットのローカル タイム ゾーンに対応する値。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

使用することも、<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>に変換するプロパティを<xref:System.DateTimeOffset>値をローカル<xref:System.DateTime>値。 <xref:System.DateTime.Kind%2A> 、返されたプロパティ<xref:System.DateTime>値は<xref:System.DateTimeKind.Local>します。 次のコードでは、<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>プロパティを変換するときに、<xref:System.DateTimeOffset>オフセットのローカル タイム ゾーンに対応する値。 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

取得する場合、<xref:System.DateTime>値を使用して、<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>プロパティ、プロパティの`get`アクセサーが最初に変換します、<xref:System.DateTimeOffset>値を UTC に変換を現地時刻に呼び出すことによって、<xref:System.DateTimeOffset.ToLocalTime%2A>メソッド。 つまりからの値を取得することができます、<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>プロパティ型の変換を実行すると同時にタイム ゾーン変換を実行します。 また、変換の実行にローカル タイム ゾーンの調整規則が適用されることも意味します。 次のコードの使用を示しています、<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>プロパティ型とタイム ゾーンの変換の両方を実行します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>汎用変換メソッド

次の例は、という名前のメソッドを定義`ConvertFromDateTimeOffset`変換<xref:System.DateTimeOffset>値<xref:System.DateTime>値。 オフセットに基づき、それを決定するかどうか、<xref:System.DateTimeOffset>値が UTC 時刻、現地時刻、またはその他のいくつかの時間と、返された日付と時刻の値の定義<xref:System.DateTime.Kind%2A>プロパティそれに応じて。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

次の例では、`ConvertFromDateTimeOffset`に変換するメソッド<xref:System.DateTimeOffset>UTC 時刻、現地時刻、および米国での時間を表す値変換します。

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

このコードは次の 2 つのことを前提としますが、アプリケーションおよびその日時値のソースによっては常に有効とは限らないことに注意してください。

* 日付と時刻値をオフセットを持つことを前提としています<xref:System.TimeSpan.Zero?displayProperty=nameWithType>UTC を表します。 実際には、UTC は特定のタイム ゾーンの時刻ではなく、世界のタイム ゾーンの時刻を標準化する際に基準となる時刻です。 タイム ゾーンのオフセットを持つことも<xref:System.TimeSpan.Zero>します。

* オフセットがローカル タイム ゾーンのオフセットと等しい日時が、ローカル タイム ゾーンを表すことを前提とします。 日時値は元のタイム ゾーンとの関連付けが解除されているので、これは該当しない場合があります。日時は、同じオフセットを持つ別のタイム ゾーンに由来する可能性があります。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
