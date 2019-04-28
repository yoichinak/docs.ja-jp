---
title: '方法: TimeZoneInfo オブジェクトをインスタンス化する'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c8ff38325e26dd1bc946f6f12c365b6dea3e228
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669174"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>方法: TimeZoneInfo オブジェクトをインスタンス化する

<xref:System.TimeZoneInfo> オブジェクトをインスタンス化する最も一般的な方法は、レジストリからオブジェクトに関する情報を取得することです。 このトピックでは、ローカル システムのレジストリから <xref:System.TimeZoneInfo> オブジェクトをインスタンス化する方法について説明します。

### <a name="to-instantiate-a-timezoneinfo-object"></a>TimeZoneInfo オブジェクトをインスタンス化するには

1. <xref:System.TimeZoneInfo> オブジェクトを宣言します。

2. `static` (Visual Basic では`Shared` ) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> メソッドを呼び出します。

3. メソッドによってスローされる例外 (特に、タイム ゾーンがレジストリで定義されていない場合にスローされる <xref:System.TimeZoneNotFoundException> ) を処理します。

## <a name="example"></a>例

次のコードでは、東部標準時のタイム ゾーンを表す <xref:System.TimeZoneInfo> オブジェクトを取得し、現地時刻に対応する東部標準時の時刻を表示します。

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> メソッドの唯一のパラメーターは、取得するタイム ゾーンの識別子です。これは、オブジェクトの <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> プロパティに対応します。 タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。 ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。 ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される <xref:System.TimeZoneInfo.StandardName%2A> オブジェクトの <xref:System.TimeZoneInfo> プロパティに対応します。 ただし、例外もあります。 有効な識別子を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、対応するタイム ゾーン識別子を記録しておくことです。 例については、次を参照してください。[方法。コンピューター上に存在するタイム ゾーンを列挙](../../../docs/standard/datetime/enumerate-time-zones.md)します。 「[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)」のトピックには、選択したタイム ゾーン ID の一覧も掲載されています。

タイム ゾーンが見つかると、メソッドは <xref:System.TimeZoneInfo> オブジェクトを返します。 タイム ゾーンが見つからない場合、メソッドから <xref:System.TimeZoneNotFoundException>がスローされます。 タイム ゾーンが見つかっても、そのデータが破損しているか不完全な場合には、メソッドから <xref:System.InvalidTimeZoneException>がスローされます。

アプリケーションが依存するタイム ゾーンが必ず存在していなければならない場合は、最初に <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを呼び出して、レジストリからタイム ゾーンの情報を取得する必要があります。 メソッドの呼び出しが失敗した場合は、例外ハンドラーで、タイム ゾーンの新しいインスタンスを作成するか、シリアル化された <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化してインスタンスを作成し直す必要があります。 「[方法:埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)例についてはします。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトにアクセスします。](../../../docs/standard/datetime/access-utc-and-local.md)
