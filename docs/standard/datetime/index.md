---
title: 日付、時刻、およびタイム ゾーン
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a5594b689a52b641ecece0f9a92fb6cdfe5735
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991287"
---
# <a name="dates-times-and-time-zones"></a>日付、時刻、およびタイム ゾーン

.NET は基本的な <xref:System.DateTime> 構造体だけでなく、タイム ゾーンでの作業をサポートする次のクラスも提供しています。

* <xref:System.TimeZone>

  システムのローカル タイム ゾーンおよび世界協定時刻 (UTC) ゾーンで作業を行うには、このクラスを使用します。 クラスの<xref:System.TimeZone>機能は、 <xref:System.TimeZoneInfo>クラスによって主に置き換えられています。

* <xref:System.TimeZoneInfo>

  このクラスを使用すると、システムに事前に定義されている任意のタイム ゾーンを処理し、新しいタイム ゾーンを作成して、1 つのタイム ゾーンから別のタイム ゾーンに日付/時刻を簡単に変換できます。 新規に開発を行う場合は、<xref:System.TimeZoneInfo> クラスではなく、<xref:System.TimeZone> クラスを使用する必要があります。

* <xref:System.DateTimeOffset>

  UTC からのオフセット (つまり時差) がわかっている日付および時刻で作業を行う場合は、この構造体を使用します。 <xref:System.DateTimeOffset> 構造体は、日付および時刻の値と、その時刻の UTC からのオフセットを組み合わせたものです。 UTC との関係により、個々の日付と時刻の値によって具体的な日時が明確に特定されます。 これにより、<xref:System.DateTime> の値よりも、<xref:System.DateTimeOffset> の値の方がコンピューター間で移植しやすくなります。

ドキュメントのこのセクションでは、タイム ゾーンでの作業を行ったり、あるタイム ゾーンから別のタイム ゾーンに日付と時刻を変換できる、タイム ゾーンに対応したアプリケーションを作成するために必要な情報を提供します。

## <a name="in-this-section"></a>このセクションの内容

[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md) タイム ゾーンに対応したアプリケーションの作成に関連する用語、概念、問題について説明します。

[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](../../../docs/standard/datetime/choosing-between-datetime.md) 日付および時刻のデータでの作業を行う場合、どのようなときに <xref:System.DateTime>、<xref:System.DateTimeOffset>、<xref:System.TimeZoneInfo> の型を使用するかについて説明します。

[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) ローカル システムで検出されたタイム ゾーンを列挙する方法について説明します。

[方法: コンピューター](../../../docs/standard/datetime/enumerate-time-zones.md)に存在するタイムゾーンを列挙する例では、コンピューターのレジストリに定義されているタイムゾーンを列挙し、ユーザーが一覧から定義済みのタイムゾーンを選択できるようにします。

[方法: 定義済みの UTC およびローカルタイムゾーンオブジェクト](../../../docs/standard/datetime/access-utc-and-local.md)にアクセスする方法については、世界協定時刻とローカルタイムゾーンにアクセスする方法を説明します。

[方法: TimeZoneInfo オブジェクト](../../../docs/standard/datetime/instantiate-time-zone-info.md)のインスタンス化ローカルシステムレジストリから<xref:System.TimeZoneInfo>オブジェクトをインスタンス化する方法について説明します。

[DateTimeOffset オブジェクトのインスタンス化](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) <xref:System.DateTimeOffset> オブジェクトをインスタンス化する方法、および <xref:System.DateTime> の値を <xref:System.DateTimeOffset> の値に変換する方法について説明します。

[方法: 調整規則](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)のないタイムゾーンを作成する夏時間との間の切り替えをサポートしないカスタムタイムゾーンを作成する方法について説明します。

[方法: 調整規則](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)が設定されたタイムゾーンを作成する夏時間との間の1つ以上の遷移をサポートするカスタムタイムゾーンを作成する方法について説明します。

[タイム ゾーンの保存と復元](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) タイム ゾーン データのシリアル化と逆シリアル化が <xref:System.TimeZoneInfo> でどのようにサポートされるかを説明し、これらの機能を使用できるいくつかのシナリオを示します。

[方法: 埋め込みリソース](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)にタイムゾーンを保存するカスタムタイムゾーンを作成し、その情報をリソースファイルに保存する方法について説明します。

[方法: 埋め込みリソース](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)からタイムゾーンを復元する埋め込みリソースファイルに保存されているカスタムタイムゾーンをインスタンス化する方法について説明します。

[日付と時刻を使用した算術演算の実行](../../../docs/standard/datetime/performing-arithmetic-operations.md) <xref:System.DateTime> および <xref:System.DateTimeOffset> の値の加算、減算、比較に関連する問題について説明します。

[方法: 日付と時刻の演算](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)でタイムゾーンを使用するタイムゾーンの調整規則を反映する日付と時刻の演算を実行する方法について説明します。

[DateTime と DateTimeOffset 間の変換](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) <xref:System.DateTime> の値と <xref:System.DateTimeOffset> の値の変換方法について説明します。

[タイム ゾーン間での時刻の変換](../../../docs/standard/datetime/converting-between-time-zones.md) タイム ゾーン間での時刻の変換方法について説明します。

[方法: あいまい](../../../docs/standard/datetime/resolve-ambiguous-times.md)な時刻を解決する時刻をタイムゾーンの標準時刻にマップして、あいまいな時刻を解決する方法について説明します。

[方法: ユーザーがあいまい](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)な時刻を解決できるようにするユーザーがあいまいな現地時刻と世界協定時刻の間のマッピングを決定できるようにする方法について説明します。

## <a name="reference"></a>参照

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
