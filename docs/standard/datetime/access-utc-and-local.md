---
title: '方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa19118ce0837b9ce0eb523f3e086fcbcecb9e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106565"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする

クラス<xref:System.TimeZoneInfo>には、 <xref:System.TimeZoneInfo.Utc%2A>とという<xref:System.TimeZoneInfo.Local%2A>2 つのプロパティが用意されており、これにより、定義済みのタイムゾーンオブジェクトにコードからアクセスできるようになります。 このトピックでは、これらのプロパティから返される <xref:System.TimeZoneInfo> オブジェクトにアクセスする方法について説明します。

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>世界協定時刻 (UTC) の TimeZoneInfo オブジェクトにアクセスするには

1. ( `static` VisualBasic`Shared` )プロパティを使用して、協定世界時に<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>アクセスします。

2. プロパティによって<xref:System.TimeZoneInfo>返されたオブジェクトをオブジェクト変数に割り当てるのではなく、 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>プロパティを使用して世界協定時刻にアクセスし続けます。

### <a name="to-access-the-local-time-zone"></a>ローカル タイム ゾーンにアクセスするには

1. ローカルシステム`static`の`Shared`タイムゾーンに<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>アクセスするには、(Visual Basic) プロパティを使用します。

2. プロパティによって<xref:System.TimeZoneInfo>返されたオブジェクトをオブジェクト変数に割り当てるのではなく、引き続き<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティを使用してローカルタイムゾーンにアクセスします。

## <a name="example"></a>例

次のコードでは<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 、 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>プロパティとプロパティを使用して、米国およびカナダ東部標準時のタイムゾーンから時刻を変換し、タイムゾーン名をコンソールに表示します。

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

ローカルタイムゾーンは、ローカルタイムゾーンを<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo>オブジェクト変数に割り当てるのではなく、常にプロパティを使用してアクセスする必要があります。 同様に、UTC ゾーン<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo>をオブジェクト変数に割り当てるのではなく、常にプロパティを使用して世界協定時刻にアクセスする必要があります。 これにより<xref:System.TimeZoneInfo> 、メソッドの<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>呼び出しによってオブジェクト変数が無効になるのを防ぐことができます。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- ステートメントを使用してC# 名前空間をインポートする(コードに必要<xref:System>) `using` 。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [方法: TimeZoneInfo オブジェクトのインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)
