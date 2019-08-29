---
title: '方法: あいまいな時刻を解決する'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e98d5d8240492ca30da2825b72277d7a35f97f6
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106784"
---
# <a name="how-to-resolve-ambiguous-times"></a>方法: あいまいな時刻を解決する

あいまいな時刻とは、複数の世界協定時刻 (UTC) にマップされる時刻です。 これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。 あいまいな時刻を処理する場合は、次のいずれかの操作を行います。

- 時刻が UTC にどのようにマップされるかを想定します。 たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。

- あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。

このトピックでは、タイムゾーンの標準時刻を表すと想定して、あいまいな時刻を解決する方法について説明します。

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>あいまいな時刻をタイム ゾーンの標準時刻にマップするには

1. <xref:System.TimeZoneInfo.IsAmbiguousTime%2A>メソッドを呼び出して、時刻があいまいであるかどうかを確認します。

2. 時刻があいまいな場合は、タイムゾーンの<xref:System.TimeSpan> <xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティによって返されたオブジェクトから時刻を減算します。

3. <xref:System.DateTime.SpecifyKind%2A> <xref:System.DateTime.Kind%2A> (Visual Basic .net で) メソッドを呼び出して、UTC の日付と時刻の値のプロパティ<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>をに設定します。`Shared` `static`

## <a name="example"></a>例

次の例は、ローカルタイムゾーンの標準時刻を表すと想定して、あいまいな時刻を UTC に変換する方法を示しています。

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

この例は、渡された`ResolveAmbiguousTime` <xref:System.DateTime>値があいまいであるかどうかを判断するという名前のメソッドで構成されています。 値があいまいな場合、メソッドは対応する<xref:System.DateTime> UTC 時刻を表す値を返します。 メソッドは、ローカルタイムゾーンの<xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティの値をローカル時刻から減算することによって、この変換を処理します。

通常、あいまいな時刻は、 <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>メソッドを呼び出して、あいまいな時刻の UTC オフセットを含むオブジェクトの<xref:System.TimeSpan>配列を取得することによって処理されます。 しかし、この例は、あいまいな時刻は常にタイム ゾーンの標準時刻にマップされるという想定に基づいています。 プロパティ<xref:System.TimeZoneInfo.BaseUtcOffset%2A>は、UTC とタイムゾーンの標準時刻の間のオフセットを返します。

この例では、ローカルタイムゾーンへのすべての参照は、 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティを使用して行われます。ローカルタイムゾーンは、オブジェクト変数に割り当てられることはありません。 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>メソッドを呼び出すと、ローカルタイムゾーンが割り当てられているオブジェクトが無効になるため、この方法をお勧めします。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- ステートメントを使用してC# 名前空間をインポートする(コードに必要<xref:System>) `using` 。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [方法: ユーザーがあいまいな時刻を解決できるようにする](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
