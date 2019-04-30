---
title: '方法: 日付と時刻の演算でタイム ゾーンを使用する'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 053ca2d10deadf58d5bb8b4628fb5dee815d82c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026498"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>方法: 日付と時刻の演算でタイム ゾーンを使用する

通常とを実行して日付時刻の算術演算を使用して<xref:System.DateTime>または<xref:System.DateTimeOffset>結果の値は、タイム ゾーン調整規則が反映されません。 日付と時刻の値のタイム ゾーンが明確に識別できる場合でもこれが true (場合など、<xref:System.DateTime.Kind%2A>プロパティに設定されて<xref:System.DateTimeKind.Local>)。 このトピックでは、特定のタイム ゾーンに属している日付と時刻の値に対する算術演算を実行する方法を示します。 算術演算の結果には、タイム ゾーンの調整規則が反映されます。

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>日付と時刻の演算に調整規則を適用するには

1. なんらかの方法を実装して、日付と時刻の値と、その値が属するタイム ゾーンを密接に結び付けます。 たとえば、日付と時刻の値とそのタイム ゾーンの両方を含む構造体を宣言します。 次の例では、このアプローチを使用してリンクする、<xref:System.DateTime>とそのタイム ゾーンの値。

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. いずれかを呼び出すことによって、時刻を世界協定時刻 (UTC) を変換、<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>メソッドまたは<xref:System.TimeZoneInfo.ConvertTime%2A>メソッド。

3. UTC 時刻で算術演算を実行します。

4. 呼び出すことによって時間を UTC から元の時刻のタイム ゾーンに変換、<xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>メソッド。

## <a name="example"></a>例

次の例では、中部標準時の 2008 年 3 月 9 日午前 1 時 30 分に、2 時間 30 分を 加えます。 夏時間へのタイム ゾーンの切り替えは、30 分後の 2008 年 3 月 9 日午前 2 時に 発生します。 この例は前に示した 4 つの手順に従うため、結果は正しい時刻である 2008 年 3 月 9 日午前 5 時に 前のコードと似ています。

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

両方<xref:System.DateTime>と<xref:System.DateTimeOffset>が属している任意のタイム ゾーンからの値は関連付けを解除します。 タイム ゾーンの調整規則が自動的に適用されるような方法で日付と時刻の演算を実行するには、日付と時刻の値の属するタイム ゾーンがすぐに識別できる状態でなければなりません。 つまり、日時と関連付けられているタイム ゾーンを密に結合する必要があります。 これは、次のようないくつかの方法で行うことができます。

* アプリケーションで使用されるすべての時刻が、特定のタイム ゾーンに属するものと仮定します。 この方法は、適切な場合もありますが、柔軟性が限られ、移植性が制限される可能性もあります。

* 日時と関連付けられているタイム ゾーンを型のフィールドとして組み込むことで、両者を密に結合する型を定義します。 コード例ではこの方法を使用して、日時とタイム ゾーンを 2 つのメンバー フィールドに格納する構造体を定義しています。

例では、算術演算を実行する方法を示しています。<xref:System.DateTime>結果にタイム ゾーン調整規則が適用されるように値。 ただし、<xref:System.DateTimeOffset>値は同じくらい簡単に使用できます。 次の例を示す方法で元の例では、コードが使用する可能性があります<xref:System.DateTimeOffset>の代わりに<xref:System.DateTime>値。

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

この加算処理は単に実行する場合、<xref:System.DateTimeOffset>最初 UTC に変換すること、結果、適切な時点の反映が、そのオフセットは反映されませんする指定されたタイム ゾーンの時点のなしの値します。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* System.Core.dll への参照をプロジェクトに追加します。

* <xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要)。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [日付と時刻を使用した算術演算の実行](../../../docs/standard/datetime/performing-arithmetic-operations.md)
