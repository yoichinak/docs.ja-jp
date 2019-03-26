---
title: タイム ゾーンの概要
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], about time zones
- transition time [.NET Framework]
- TimeZoneInfo class, about TimeZoneInfo class
- time zones [.NET Framework], creating
- invalid time [.NET Framework]
- fixed rule [.NET Framework]
- ambiguous time [.NET Framework]
- floating rule [.NET Framework]
- daylight saving time [.NET Framework]
- adjustment rule [.NET Framework]
- time zones [.NET Framework], terminology
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5fa4376cdb0496cfd25f4764257c4f3afbc7268
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697050"
---
# <a name="time-zone-overview"></a>タイム ゾーンの概要

<xref:System.TimeZoneInfo>クラスは、タイム ゾーン対応アプリケーションの作成を簡略化します。 <xref:System.TimeZone>クラスのローカル タイム ゾーンと世界協定時刻 (UTC) での作業をサポートしています。 <xref:System.TimeZoneInfo>クラスでは、これらのゾーンに関する情報だけでなく、タイム ゾーンがレジストリに定義済みの両方がサポートされます。 使用することも<xref:System.TimeZoneInfo>システムに関する情報がないカスタムのタイム ゾーンを定義します。

## <a name="time-zone-essentials"></a>タイム ゾーンの基本

タイム ゾーンは、同じ時刻が使用されている地域です。 常にではありませんが、通常、隣接するタイム ゾーンは 1 時間違いです。 世界のタイム ゾーンの時刻は、世界協定時刻 (UTC) からのオフセットとして表されます。

世界のタイム ゾーンの多くは、夏時間をサポートしています。 夏時間では、春や初夏には時刻を 1 時間進め、晩夏や秋には通常 (または標準) の時間に戻すことで、日中の時間を最大化しようと試みます。 こうした標準時間前後の変更は、調整規則と呼ばれます。

特定のタイム ゾーンの夏時間前後の移行は、固定調整規則または浮動調整規則で定義できます。 固定調整規則では、毎年、夏時間前後の移行が行われる特定の日付を設定します。 たとえば、毎年 10 月 25 日に行われる夏時間から標準時間への移行は、固定調整規則に従います。 浮動調整規則の方がはるかに一般的です。浮動調整規則では、夏時間への移行、または夏時間からの移行について特定の月の特定の週の特定の曜日が設定されます。 たとえば、3 月の第 3 日曜日に行われる標準時間から夏時間への移行は、浮動調整規則に従います。

調整規則をサポートするタイム ゾーンの場合、夏時間前後の移行によって、2 つの変則的な時刻が生じます。無効な時刻とあいまいな時刻です。 無効な時刻は、標準時間から夏時間への移行で生じる存在しない時刻です。 たとえば、移行が特定の日付の午前 2:00 に行われ、 時刻が午前 3:00 に変更される場合、午前 2:00 から 午前 2:59:99 までの時刻は 無効です。 あいまいな時刻は、1 つのタイム ゾーンで 2 つの時刻にマップできる時刻です。 あいまいな時刻は夏時間から標準時間への移行で生じます。 たとえば、移行が特定の日付の午前 2:00 に行われ、 時刻が午前 1:00 に変更される場合、午前 1:00 から 午前 1:59:99 までの時刻は 標準時間または夏時間のいずれにでも解釈できます。

## <a name="time-zone-terminology"></a>タイム ゾーンの用語

次の表は、タイム ゾーンを使用し、タイム ゾーン対応アプリケーションを開発するときに一般的に使用される用語の定義一覧です。

| 用語            | 定義 |
| --------------- | ---------- |
| 調整規則 | 標準時間から夏時間へ、および夏時間から標準時間への移行が行われるタイミングを定義した規則。 各調整規則がときに、ルールが設定を定義する開始と終了日 (たとえば、1986 年 1 月 1日から 2006 年 12 月 31 日までのインプレースは調整規則)、デルタ (番目のアプリケーションの結果として標準時に変更する時間の長さe の調整規則) については、特定の日付と時刻調整期間中に発生する遷移であるとします。 移行は、固定規則または浮動規則に従う可能性があります。 |
| あいまいな時刻  | 1 つのタイム ゾーンで 2 つの時刻にマップできる時刻です。 あいまいな時刻は、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。 たとえば、移行が特定の日付の午前 2:00 に行われ、 時刻が午前 1:00 に変更される場合、午前 1:00 から 午前 1:59:99 までの時刻は 標準時間または夏時間のいずれにでも解釈できます。 |
| 固定規則      | 夏時間前後の移行について特定の日付を設定する調整規則。 たとえば、毎年 10 月 25 日に行われる夏時間から標準時間への移行は、固定調整規則に従います。 |
| 浮動規則   | 浮動調整規則の方がはるかに一般的です。浮動調整規則では、夏時間への移行、または夏時間からの移行について特定の月の特定の週の特定の曜日が設定されます。 たとえば、3 月の第 3 日曜日に行われる標準時間から夏時間への移行は、浮動調整規則に従います。 |
| 無効な時刻    | 標準時間から夏時間への移行中に生じる存在しない時刻。 無効な時刻は、あるタイム ゾーンの標準時間から夏時間に移行する際など、時計の時刻を前に進めるときに発生します。 たとえば、移行が特定の日付の午前 2:00 に行われ、 時刻が午前 3:00 に変更される場合、午前 2:00 から 午前 2:59:99 までの時刻は 無効です。 |
| 移行時間 | 特定のタイム ゾーンで実施される夏時間と標準時間の切り替えなど、特定の時間切り替えに関する情報。 |

## <a name="time-zones-and-the-timezoneinfo-class"></a>タイム ゾーンと TimeZoneInfo クラス

.NET を<xref:System.TimeZoneInfo>オブジェクトは、タイム ゾーンを表します。 <xref:System.TimeZoneInfo>クラスが含まれています、<xref:System.TimeZoneInfo.GetAdjustmentRules%2A>の配列を返すメソッド<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクト。 この配列の各要素は、特定の期間と夏時間の間の切り替えに関する情報を提供します。 (夏時間をサポートしていないタイム ゾーンの場合、メソッドを返します、空の配列。)各<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクトには、<xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A>と<xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A>と夏時間の間に、特定の日付と、遷移の時間を定義するプロパティです。 <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A>プロパティは、その遷移は、固定または浮動小数点かどうかを示します。

.NET では、Windows オペレーティング システムによって提供され、レジストリに格納されているタイム ゾーン情報に依存しています。 地球のタイム ゾーンの数、原因は、既存のすべてのタイム ゾーンがレジストリで表されます。 さらに、レジストリが動的な構造であるため、定義済みのタイム ゾーンに追加したりから削除します。 最後に、レジストリは必ずしもありません過去のタイム ゾーンのデータ。 たとえば、Windows XP には、レジストリには、タイム ゾーン調整の 1 つのセットのみに関するデータが含まれています。 Windows Vista では、1 つのタイム ゾーンが年の特定の間隔に適用される複数の調整規則を持つことができることを意味するタイム ゾーンの動的なデータをサポートします。 ただし、Windows Vista レジストリとサポート夏時間で定義されているほとんどのタイム ゾーンでは、1 つまたは 2 つの定義済みの調整規則があります。

依存関係、<xref:System.TimeZoneInfo>レジストリのクラスがすることはできません、タイム ゾーンに対応するアプリケーションが特定の特定のタイム ゾーンがレジストリで定義されていることを意味します。 そのため、(ローカルのタイム ゾーンまたは UTC を示すタイム ゾーン以外の) 特定のタイム ゾーンをインスタンス化する場合、例外処理を使用する必要があります。 アプリケーションを必要な場合に続行できる何らかの方法も提供する必要があります<xref:System.TimeZoneInfo>レジストリからオブジェクトをインスタンス化することはできません。

必要なタイム ゾーンでは、休暇を処理するために、<xref:System.TimeZoneInfo>クラスが含まれています、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドで、レジストリにも記載されていないカスタムのタイム ゾーンを作成して使用することができます。 カスタムのタイム ゾーンの作成の詳細については、[方法。調整規則のないタイム ゾーンを作成](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)と[方法。タイム ゾーン調整規則を作成](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)を参照してください。 さらに、使用、<xref:System.TimeZoneInfo.ToSerializedString%2A>メソッドを新しく作成されたタイム ゾーンを文字列に変換し、(データベース、テキスト ファイル、レジストリ、またはアプリケーションのリソース) などのデータ ストアに保存します。 使用することができますし、<xref:System.TimeZoneInfo.FromSerializedString%2A>にこの文字列に変換するメソッドが戻る、<xref:System.TimeZoneInfo>オブジェクト。 詳細については、[方法。埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)と[方法。埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)を参照してください。

各タイム ゾーンは、UTC からのベース オフセットと、既存の調整規則を反映した UTC からのオフセットによって表されるため、あるタイム ゾーンの時刻は、簡単に別のタイム ゾーンの時間に変換できます。 この目的で、<xref:System.TimeZoneInfo>オブジェクトにはなど、いくつかの変換メソッドが含まれています。

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>を指定したタイム ゾーンの時刻を UTC に変換します。

* <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>を指定したタイム ゾーンの時刻を UTC に変換します。

* <xref:System.TimeZoneInfo.ConvertTime%2A>で指定された別のタイム ゾーンの時刻に 1 つの指定されたタイム ゾーンの時刻に変換します。

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>、タイム ゾーン id を使用する (の代わりに<xref:System.TimeZoneInfo>オブジェクト) を指定した別のタイム ゾーンの時刻に 1 つの指定されたタイム ゾーンの時刻を変換するパラメーターとして。

タイム ゾーン間の時間を変換する方法の詳細については、「[タイム ゾーン間での時刻の変換](../../../docs/standard/datetime/converting-between-time-zones.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
