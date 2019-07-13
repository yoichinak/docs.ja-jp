---
title: '方法: 調整規則のあるタイム ゾーンを作成する'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: face995dbd5ba4b0b12e80bcef10a90b46c093ff
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586415"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>方法: 調整規則のあるタイム ゾーンを作成する

アプリケーションで必要とされる正確なタイム ゾーン情報は、いくつかの理由で特定のシステムに存在しない場合があります。

* タイム ゾーンがローカル システムのレジストリで定義されていません。

* タイム ゾーンに関するデータが変更されたか、レジストリから削除します。

* タイム ゾーンには、過去の特定の期間のタイム ゾーンの調整に関する正確な情報はありません。

このような場合を呼び出すことができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>アプリケーションに必要なタイム ゾーンを定義するメソッド。 このメソッドのオーバー ロードを使用すると、調整規則の有無、タイム ゾーンを作成します。 タイム ゾーンが夏時間をサポートする場合は、いずれかの固定長または浮動調整規則の調整を定義できます。 (これらの用語の定義は、「タイム ゾーンの用語」のセクションを参照してください[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)。)。

> [!IMPORTANT]
> 呼び出すことによって作成されたカスタムのタイム ゾーン、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドは、レジストリに追加されません。 代わりに、によって返されるオブジェクトの参照を介してのみアクセスすることができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドの呼び出し。

このトピックでは、調整規則のあるタイム ゾーンを作成する方法を示します。 夏時間調整規則がサポートされていないタイム ゾーンを作成するを参照してください。[方法。調整規則のないタイム ゾーンを作成](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)です。

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>浮動調整規則のあるタイム ゾーンを作成するには

1. 調整 (つまりは、各遷移から離れると標準時に、特定の時間間隔の間) ごとに、次の操作を行います。

    1. タイム ゾーン調整の切り替えの開始時刻を定義します。

       呼び出す必要があります、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>メソッドを渡して、 <xref:System.DateTime> 、遷移、遷移の月を定義する整数値、遷移が発生する曜日を定義する整数値の時刻を定義する値と<xref:System.DayOfWeek>遷移が発生する曜日を定義する値。 このメソッドの呼び出しをインスタンス化、<xref:System.TimeZoneInfo.TransitionTime>オブジェクト。

    2. タイム ゾーン調整の切り替えの終了時刻を定義します。 別の呼び出しを必要があります、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>メソッド。 このメソッドを呼び出す 2 つ目のインスタンスを作成<xref:System.TimeZoneInfo.TransitionTime>オブジェクト。

    3. 呼び出す、<xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A>メソッドを渡して、有効な開始と終了日、調整の<xref:System.TimeSpan>遷移、および 2 つの時間を定義するオブジェクト<xref:System.TimeZoneInfo.TransitionTime>タイミングを定義するオブジェクトと夏時間の間の遷移時間が発生します。 このメソッドの呼び出しをインスタンス化、<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクト。

    4. 割り当てる、<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクトの配列を<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクト。

2. タイム ゾーンの表示名を定義します。 表示名を世界協定時刻 (UTC) からのタイム ゾーンのオフセットがかっこで囲まれているし、タイム ゾーンを 1 つまたは複数のタイム ゾーン、または 1 つの都市または、cou の詳細を識別する文字列の後に、ごく標準的な形式に依存します。ntries またはタイム ゾーン内の領域。

3. タイム ゾーンの標準時刻の名前を定義します。 通常、この文字列は、タイム ゾーンの識別子としても使用します。

4. タイム ゾーンの夏時間の名前を定義します。

5. タイム ゾーンの標準の名前とは異なる id を使用する場合は、タイム ゾーン id を定義します。

6. インスタンスを作成、 <xref:System.TimeSpan> UTC からのタイム ゾーンのオフセットを定義するオブジェクト。 UTC より後の時刻のタイム ゾーン オフセットを正の値があります。 時刻は UTC よりも前のタイム ゾーンでは、負のオフセットがあります。

7. 呼び出す、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>新しいタイム ゾーンをインスタンス化するメソッド。

## <a name="example"></a>例

次の例では、さまざまな 1918年から現在までの時間間隔の調整規則を含む米国の中部標準時ゾーンを定義します。

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

この例で作成したタイム ゾーンでは、複数の調整規則があります。 有効な開始と終了日の任意の調整規則は別の調整規則の日付で重複していないことを確認する注意する必要があります。 、重複がある場合、<xref:System.InvalidTimeZoneException>がスローされます。

渡される 5 の値の浮動調整規則を`week`のパラメーター、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>メソッドを特定の月の最終週の遷移が発生することを示します。

配列を作成することで<xref:System.TimeZoneInfo.AdjustmentRule>で使用するオブジェクト、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>メソッドの呼び出し、コードは、初期化、調整の数とタイム ゾーンの作成に必要なサイズの配列。 このコード例では、代わりに、<xref:System.Collections.Generic.List%601.Add%2A>ジェネリックに各調整規則を追加するメソッド<xref:System.Collections.Generic.List%601>のコレクション<xref:System.TimeZoneInfo.AdjustmentRule>オブジェクト。 コードを呼び出して、<xref:System.Collections.Generic.List%601.CopyTo%2A>メソッドをこのコレクションのメンバーを配列にコピーします。

また、例では、<xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A>固定日付の調整を定義するメソッド。 これは、呼び出しに似ています、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>ことは、時間、月、および遷移パラメーターの 1 日のみが必要です。 ただし、メソッド。

例は、次のコードを使用してテストできます。

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* 次の名前空間は、インポートします。

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
- [方法: 調整規則のないタイム ゾーンを作成します。](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
