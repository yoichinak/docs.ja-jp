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
ms.openlocfilehash: d36b5ff4912b09101694dd0e83291053260f0bf9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586422"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする

<xref:System.TimeZoneInfo>クラスは、2 つのプロパティを提供します。<xref:System.TimeZoneInfo.Utc%2A>と<xref:System.TimeZoneInfo.Local%2A>、定義済みのタイム ゾーン オブジェクトへのコード アクセス権を付与します。 このトピックでは、これらのプロパティから返される <xref:System.TimeZoneInfo> オブジェクトにアクセスする方法について説明します。

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>世界協定時刻 (UTC) の TimeZoneInfo オブジェクトにアクセスするには

1. 使用して、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>世界協定時刻にアクセスするプロパティ。

2. 割り当てではなく、<xref:System.TimeZoneInfo>引き続きを世界協定時刻にアクセスするオブジェクトが、オブジェクト変数に、プロパティによって返される、<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>プロパティ。

### <a name="to-access-the-local-time-zone"></a>ローカル タイム ゾーンにアクセスするには

1. 使用して、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>ローカル システムのタイム ゾーンにアクセスするプロパティ。

2. 割り当てではなく、<xref:System.TimeZoneInfo>引き続きを通じて、ローカル タイム ゾーンにアクセスするオブジェクトが、オブジェクト変数に、プロパティによって返される、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティ。

## <a name="example"></a>例

次のコードでは、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>と<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>米国およびカナダ東部標準時ゾーンの時刻を変換するだけでなく、タイム ゾーン名をコンソールに表示するプロパティ。

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

使用してローカル タイム ゾーンを常にアクセスする必要があります、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>にゾーンのローカル時刻を割り当てるのではなく、プロパティ、<xref:System.TimeZoneInfo>オブジェクト変数です。 同様に、アクセスするには常に協定世界時で、<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>にゾーンの UTC を割り当てるのではなく、プロパティ、<xref:System.TimeZoneInfo>オブジェクト変数です。 これにより、<xref:System.TimeZoneInfo>オブジェクト変数への呼び出しによって無効になることから、<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>メソッド。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* <xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要)。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [方法: TimeZoneInfo オブジェクトをインスタンス化します。](../../../docs/standard/datetime/instantiate-time-zone-info.md)
