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
ms.openlocfilehash: aae3e5145d2fa85cd55fc5b1288ef4aaa0fef48f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796410"
---
# <a name="how-to-resolve-ambiguous-times"></a>方法: あいまいな時刻を解決する

あいまいな時刻とは、複数の世界協定時刻 (UTC) にマップされる時刻です。 これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。 あいまいな時刻を処理する場合は、次のいずれかの操作を行います。

* 時刻が UTC にどのようにマップされるかを想定します。 たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。

* あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。

このトピックでは、タイム ゾーンの標準時刻を表すと想定してあいまいな時刻を解決する方法を示します。

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>あいまいな時刻をタイム ゾーンの標準時刻にマップするには

1. 呼び出す、<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>時刻があいまいかどうかを判断するメソッド。

2. 時間を時刻があいまいな場合は、減算、<xref:System.TimeSpan>タイム ゾーンのによって返されるオブジェクト<xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティ。

3. 呼び出す、 `static` (`Shared` Visual Basic .net)<xref:System.DateTime.SpecifyKind%2A>メソッド、UTC の日付と時刻の値の設定を<xref:System.DateTime.Kind%2A>プロパティを<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>します。

## <a name="example"></a>例

次の例では、ローカル タイム ゾーンの標準時刻を表すと仮定すると、あいまいな時刻を UTC に変換する方法を示します。

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

例では、という名前のメソッドから成る`ResolveAmbiguousTime`を決定するかどうか、<xref:System.DateTime>は渡された値があいまいです。 値があいまい、メソッドを返します、<xref:System.DateTime>対応する UTC 時刻を表す値です。 メソッドでは、この変換を処理のローカル タイム ゾーンの値を減算<xref:System.TimeZoneInfo.BaseUtcOffset%2A>からローカル時刻のプロパティ。

呼び出すことによって、あいまいな時刻を処理する、通常、<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>の配列を取得するメソッドを<xref:System.TimeSpan>あいまいな時刻の考えられる UTC が含まれているオブジェクトのオフセットします。 しかし、この例は、あいまいな時刻は常にタイム ゾーンの標準時刻にマップされるという想定に基づいています。 <xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティは、UTC とタイム ゾーンの標準時刻の間のオフセットを返します。

この例では、ローカル タイム ゾーンへのすべての参照によって行われた、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティです。 ローカルのタイム ゾーンは、オブジェクト変数に割り当てられません。 これは、ためにの推奨される方法への呼び出し、<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>メソッドにローカル タイム ゾーンが割り当てられているすべてのオブジェクトが無効になります。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* System.Core.dll への参照をプロジェクトに追加します。

* <xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要)。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [方法: ユーザーがあいまいな時刻を解決できるように](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
