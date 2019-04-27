---
title: '方法: 調整規則のないタイム ゾーンを作成する'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3ffc7b6f1f7baec7ce6beb5a50b706ff78bfa1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026550"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>方法: 調整規則のないタイム ゾーンを作成する

アプリケーションで必要とされる正確なタイム ゾーン情報は、いくつかの理由で特定のシステムに存在しない場合があります。

* タイム ゾーンがローカル システムのレジストリで定義されていません。

* タイム ゾーンに関するデータが変更されたか、レジストリから削除します。

* タイム ゾーンが存在しますが、過去の特定の期間のタイム ゾーンの調整に関する正確な情報はありません。

このような場合を呼び出すことができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>アプリケーションに必要なタイム ゾーンを定義するメソッド。 このメソッドのオーバー ロードを使用すると、調整規則の有無、タイム ゾーンを作成します。 タイム ゾーンが夏時間をサポートする場合は、いずれかの固定長または浮動調整規則の調整を定義できます。 (これらの用語の定義は、「タイム ゾーンの用語」のセクションを参照してください[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)。)。

> [!IMPORTANT]
> 呼び出すことによって作成されたカスタムのタイム ゾーン、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドは、レジストリに追加されません。 代わりに、によって返されるオブジェクトの参照を介してのみアクセスすることができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドの呼び出し。

このトピックでは、調整規則のないタイム ゾーンを作成する方法を示します。 夏時間調整規則をサポートするタイム ゾーンを作成するを参照してください。[方法。タイム ゾーン調整規則を作成](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)です。

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>調整規則のないタイム ゾーンを作成するには

1. タイム ゾーンの表示名を定義します。

   表示名を世界協定時刻 (UTC) からのタイム ゾーンのオフセットがかっこで囲まれているし、タイム ゾーンを 1 つまたは複数のタイム ゾーン、または 1 つの都市または、cou の詳細を識別する文字列の後に、ごく標準的な形式に依存します。ntries またはタイム ゾーン内の領域。

2. タイム ゾーンの標準時刻の名前を定義します。 通常、この文字列は、タイム ゾーンの識別子としても使用します。

3. タイム ゾーンの標準の名前とは異なる id を使用する場合は、タイム ゾーン id を定義します。

4. インスタンスを作成、 <xref:System.TimeSpan> UTC からのタイム ゾーンのオフセットを定義するオブジェクト。 UTC より後の時刻のタイム ゾーン オフセットを正の値があります。 時刻は UTC よりも前のタイム ゾーンでは、負のオフセットがあります。

5. 呼び出す、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>新しいタイム ゾーンをインスタンス化するメソッド。

## <a name="example"></a>例

次の例は、モーソン、南極、調整規則がないカスタム タイム ゾーンを定義します。

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

割り当てられた文字列、<xref:System.TimeZoneInfo.DisplayName%2A>プロパティが UTC からのタイム ゾーンのオフセットがタイム ゾーンのわかりやすい説明の後に、標準形式に従います。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* System.Core.dll への参照をプロジェクトに追加します。

* 次の名前空間は、インポートします。

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
- [方法: タイム ゾーン調整規則を作成します。](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
