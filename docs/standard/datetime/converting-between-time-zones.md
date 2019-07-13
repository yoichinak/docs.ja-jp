---
title: タイム ゾーン間での時刻の変換
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e08e90f61429f01f360808866fdc3d963323ba23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61901819"
---
# <a name="converting-times-between-time-zones"></a>タイム ゾーン間での時刻の変換

日時を使用するすべてのアプリケーションで、タイム ゾーン間の違いを処理することの重要性が高まっています。 アプリケーションは、するすべての時刻で表現できるローカル時刻を不要になった想定できますが、時間がから利用可能な<xref:System.DateTime>構造体。 たとえば、米国東部の現在の時刻を表示する Web ページには、東アジアの顧客に対する信頼性を欠いています。 このトピックでは、時間を別の 1 つのタイム ゾーンに変換する方法と、変換する方法について説明します。<xref:System.DateTimeOffset>タイム ゾーンに対応が限られている値。

## <a name="converting-to-coordinated-universal-time"></a>世界協定時刻への変換

世界協定時刻 (UTC) は、高精度の原子時標準です。 世界のタイム ゾーンは、UTC からの正または負のオフセットとして表現されます。 したがって、UTC はタイム ゾーンの影響を受けない、またはタイム ゾーンに依存しない種類の時刻を提供します。 コンピューター間の日時の移植性が重要となる場合には、UTC 時刻の使用が推奨されます。 (詳細および日付と時刻を使用して他のベスト プラクティスでは、次を参照してください[コーディングのベスト プラクティスが .NET Framework で DateTime を使用した](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10))。)。個別のタイム ゾーンを UTC に変換すると、時間の比較が容易になります。

> [!NOTE]
> シリアル化することも、<xref:System.DateTimeOffset>を明確に単一ポイントを表す構造体。 <xref:System.DateTimeOffset> UTC からのオフセットと共に日付と時刻の値を格納するオブジェクトを常に、特定の時点を表してリレーションシップで UTC にします。

時刻を UTC に変換する最も簡単な方法を呼び出す、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>メソッド。 メソッドによって実行される正確な変換の値によって異なります、`dateTime`パラメーターの<xref:System.DateTime.Kind%2A>プロパティとして、次の表に示します。

| `DateTime.Kind`            | 変換                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | 現地時刻を UTC に変換します。                                                    |
| `DateTimeKind.Unspecified` | `dateTime` パラメーターが現地時刻であることを前提とし、現地時刻を UTC に変換します。 |
| `DateTimeKind.Utc`         | `dateTime` パラメーターを変更せずに返します。                                    |

次のコードは、現在の現地時刻を UTC に変換し、コンソールに結果を表示します。

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

日付と時刻の値が現地時刻と utc のどちらのいずれかを表していない場合、<xref:System.DateTime.ToUniversalTime%2A>メソッドは、誤った結果を返す可能性があります。 ただし、使用することができます、<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>指定されたタイム ゾーンから日付と時刻に変換します。 (詳細を取得する方法について、<xref:System.TimeZoneInfo>変換先タイム ゾーンを表すオブジェクトを参照してください[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md))。次のコードでは、<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>東部標準時を UTC に変換します。

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

このメソッドがスローされますが、<xref:System.ArgumentException>場合、<xref:System.DateTime>オブジェクトの<xref:System.DateTime.Kind%2A>プロパティとタイム ゾーンが一致しません。 場合に、不一致が発生、<xref:System.DateTime.Kind%2A>プロパティは<xref:System.DateTimeKind.Local?displayProperty=nameWithType>が、<xref:System.TimeZoneInfo>オブジェクトは、ローカル タイム ゾーンを表していません場合は、<xref:System.DateTime.Kind%2A>プロパティは<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>が、<xref:System.TimeZoneInfo>オブジェクトが等しくない<xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>します。

これらのメソッドのすべてにかかる<xref:System.DateTime>パラメーターと戻り値として値を<xref:System.DateTime>値。 <xref:System.DateTimeOffset>値、<xref:System.DateTimeOffset>構造体が、<xref:System.DateTimeOffset.ToUniversalTime%2A>インスタンスの現在のインスタンスの日時を UTC に変換するメソッド。 次の例では、<xref:System.DateTimeOffset.ToUniversalTime%2A>現地時刻と他のいくつかの時刻を世界協定時刻 (UTC) に変換します。

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>UTC から指定したタイム ゾーンへの変換

UTC を現地時刻に変換するには、次の「に変換する UTC から現地時刻」セクションを参照してください。 UTC に変換することを指定している任意のタイム ゾーンの時刻に呼び出し、<xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>メソッド。 このメソッドは、次の 2 つのパラメーターを受け取ります。

* 変換対象の UTC。 これは、必要があります、<xref:System.DateTime>値<xref:System.DateTime.Kind%2A>プロパティに設定されて`Unspecified`または`Utc`します。

* UTC の変換先のタイム ゾーン。

次のコードは、UTC を中部標準時に変換します。

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>UTC から現地時刻への変換

UTC を現地時刻に変換するには、呼び出し、<xref:System.DateTime.ToLocalTime%2A>のメソッド、<xref:System.DateTime>オブジェクトに変換する時刻。 メソッドの正確な動作は、オブジェクトの値によって異なります。<xref:System.DateTime.Kind%2A>プロパティとして、次の表に示します。

| `DateTime.Kind`            | 変換                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | 返します、<xref:System.DateTime>値は変更されません。                                      |
| `DateTimeKind.Unspecified` | 前提としています、<xref:System.DateTime>値は UTC であり、UTC を現地時刻に変換します。 |
| `DateTimeKind.Utc`         | 変換、<xref:System.DateTime>を現地時刻の値。                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType>メソッドの動作、`DateTime.ToLocalTime`メソッド。 これは、これは、日付と時刻の値に変換する 1 つのパラメーター。

使用して、ローカル時刻では、指定されたタイム ゾーンの時刻を変換することも、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType>メソッド。 この手法は、次のセクションで説明します。

## <a name="converting-between-any-two-time-zones"></a>任意の 2 つのタイム ゾーン間での変換

次の 2 つのいずれかを使用して、2 つのタイム ゾーン間で変換できる`static`(`Shared` Visual basic) のメソッド、<xref:System.TimeZoneInfo>クラス。

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  このメソッドのパラメーターは、変換する日付と時刻の値を`TimeZoneInfo`日付と時刻の値のタイム ゾーンを表すオブジェクトを`TimeZoneInfo`に日付と時刻の値を変換先タイム ゾーンを表すオブジェクト。

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  このメソッドのパラメーターに日付と時刻の値に変換する日付と時刻値に変換するの日付と時刻の値のタイム ゾーンの識別子およびタイム ゾーンの識別子。

どちらの方法では、する必要があります、<xref:System.DateTime.Kind%2A>に変換する日付と時刻の値のプロパティと<xref:System.TimeZoneInfo>そのタイム ゾーンを表すオブジェクトまたはタイム ゾーンの識別子が相互に対応します。 それ以外の場合は、<xref:System.ArgumentException> がスローされます。 たとえば場合、`Kind`日付と時刻の値のプロパティが`DateTimeKind.Local`場合に、例外がスローされます、`TimeZoneInfo`メソッドにパラメーターとして渡されたオブジェクトが等しくない`TimeZoneInfo.Local`します。 メソッドにパラメーターとして渡された識別子が等しくない場合にも、例外がスロー`TimeZoneInfo.Local.Id`します。

次の例では、<xref:System.TimeZoneInfo.ConvertTime%2A>ハワイ標準時を現地時刻に変換します。

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>DateTimeOffset 値の変換

によって表された日付と時刻の値<xref:System.DateTimeOffset>オブジェクトが完全にタイム ゾーン オブジェクトが、時にそのタイム ゾーンから切り離されるため、注意してください。 インスタンス化されます。 ただし、アプリケーションでは多くの場合、特定のタイム ゾーンの時刻ではなく、単に UTC からの 2 つの異なるオフセットに基づいて日時を変換する必要があります。 この変換を実行するには、現在のインスタンスを呼び出すことができます<xref:System.DateTimeOffset.ToOffset%2A>メソッド。 メソッドの 1 つのパラメーターは、新しい日付と時刻の値を返すメソッドのオフセットです。

たとえば、Web ページに対するユーザー要求の日時が既知であり、MM/dd/yyyy hh:mm:ss zzzz の形式で文字列としてシリアル化される場合、次の `ReturnTimeOnServer` メソッドは、この日時値を Web サーバー上の日時に変換します。

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

このメソッドが、UTC よりも 5 時間遅いタイム ゾーンの日時を表す文字列 "9/1/2007 5:32:07 -05:00" を渡された場合、米国の太平洋標準時ゾーンにあるサーバー用に 9/1/2007 3:32:07 AM -07:00 を太平洋標準時ゾーンでの実行例を次に示します。

<xref:System.TimeZoneInfo>クラスには、オーバー ロードも含まれています、<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>メソッドを使用するタイム ゾーン変換を実行する<xref:System.DateTimeOffset.ToOffset(System.TimeSpan)>値。 メソッドのパラメーターは、<xref:System.DateTimeOffset>値と時刻の変換先タイム ゾーンへの参照。 メソッド呼び出しが返されます、<xref:System.DateTimeOffset>値。 たとえば、`ReturnTimeOnServer`を呼び出す前の例のメソッドを次のように書き換えることができます、<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29>メソッド。

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>関連項目

- <xref:System.TimeZoneInfo>
- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
