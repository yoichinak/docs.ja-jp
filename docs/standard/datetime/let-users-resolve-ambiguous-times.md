---
title: '方法: ユーザーがあいまいな時刻を解決できるようにする'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70c73de068e067501cd4b1e5f80f85639e790ee2
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586389"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>方法: ユーザーがあいまいな時刻を解決できるようにする

あいまいな時刻とは、複数の世界協定時刻 (UTC) にマップされる時刻です。 これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。 あいまいな時刻を処理する場合は、次のいずれかの操作を行います。

* あいまいな時刻が、ユーザーによって入力されたデータの項目の場合は、あいまいさの解決をユーザーに任せることができます。

* 時刻が UTC にどのようにマップされるかを想定します。 たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。

このトピックでは、ユーザーにあいまいな時刻を解決できるようにする方法を示します。

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>ユーザーにあいまいな時刻を解決させるには

1. ユーザーによって入力された日付と時刻を取得します。

2. 呼び出す、<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>時刻があいまいかどうかを判断するメソッド。

3. 時刻があいまいな場合は、呼び出し、<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>の配列を取得するメソッドを<xref:System.TimeSpan>オブジェクト。 配列内の各要素には、あいまいな時刻にマップできる UTC オフセットが含まれています。

4. ユーザーに目的のオフセットを選択させます。

5. ローカル時刻からユーザーによって選択されたオフセットを減算して、UTC の日時を取得します。

6. 呼び出す、 `static` (`Shared` Visual Basic .net)<xref:System.DateTime.SpecifyKind%2A>メソッド、UTC の日付と時刻の値の設定を<xref:System.DateTime.Kind%2A>プロパティを<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>します。

## <a name="example"></a>例

次の例では、ユーザーに日付と時刻を入力するように求め、それがあいまいである場合は、ユーザーにあいまいな時刻をマップする UTC 時刻を選択させています。

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

コード例のコアの配列を使用して<xref:System.TimeSpan>あいまいな時刻を UTC からの可能性のあるオフセットを示すオブジェクト。 ただし、これらのオフセットは、ユーザーにとって意味がない可能性があります。 オフセットの意味を明確にするには、コードで、オフセットがローカル タイム ゾーンの標準時刻を表すか、または夏時間を表すかに注意します。 標準には、コードの決定し、オフセットには、値を比較することで夏時間に移行するには、<xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティ。 このプロパティは、UTC とタイム ゾーンの標準時間の差を示します。

この例では、ローカル タイム ゾーンへのすべての参照によって行われた、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティです。 ローカルのタイム ゾーンは、オブジェクト変数に割り当てられません。 これは、ためにの推奨される方法への呼び出し、<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>メソッドにローカル タイム ゾーンが割り当てられているすべてのオブジェクトが無効になります。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* <xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要)。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [方法: あいまいな時刻を解決するには](../../../docs/standard/datetime/resolve-ambiguous-times.md)
