---
title: タイム ゾーンの保存と復元
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d783f9e0d098e472dcf67aea394804d6eef2662
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026524"
---
# <a name="saving-and-restoring-time-zones"></a>タイム ゾーンの保存と復元

<xref:System.TimeZoneInfo>クラスが定義済みのタイム ゾーン データを取得するレジストリに依存します。 ただし、レジストリは、動的な構造です。 さらに、レジストリを含むタイム ゾーン情報は、現在の年の時刻の調整および変換を処理するには、主に、オペレーティング システムによって使用されます。 これは、正確なタイム ゾーン データに依存するアプリケーションの 2 つの主要な影響があります。

* アプリケーションで必要とされるタイム ゾーンがレジストリに定義されていませんが、または名前が変更されているか、レジストリから削除します。

* レジストリで定義されているタイム ゾーンは、過去のタイム ゾーン変換のために必要な特定の調整ルールに関する情報がない可能性があります。

<xref:System.TimeZoneInfo>クラス (保存) をシリアル化および逆シリアル化のタイム ゾーンのデータを (復元) のサポートにより、これらの制限に対処します。

## <a name="time-zone-serialization-and-deserialization"></a>タイム ゾーンのシリアル化および逆シリアル化

保存とタイム ゾーンのデータをシリアル化およびタイム ゾーンを復元するには、2 つのメソッド呼び出しにはが含まれます。

* シリアル化することができます、<xref:System.TimeZoneInfo>オブジェクトを呼び出して、そのオブジェクトの<xref:System.TimeZoneInfo.ToSerializedString%2A>メソッド。 メソッドは、パラメーターを受け取らないし、タイム ゾーン情報を含む文字列を返します。

* 逆シリアル化することができます、<xref:System.TimeZoneInfo>にその文字列を渡すことによってシリアル化された文字列からオブジェクト、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType>メソッド。

## <a name="serialization-and-deserialization-scenarios"></a>シリアル化および逆シリアル化シナリオ

保存 (またはシリアル化) する機能、<xref:System.TimeZoneInfo>後で使用できる文字列と復元 (または逆シリアル化) にそのオブジェクトは、ユーティリティとの柔軟性の両方が増加、<xref:System.TimeZoneInfo>クラス。 このセクションでは、一部のシリアル化および逆シリアル化は最も役に立つ状況を調べます。

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>シリアル化して、アプリケーションでのタイム ゾーン データを逆シリアル化

必要がある場合、文字列からシリアル化されたタイム ゾーンを復元できます。 レジストリから取得するタイム ゾーンが特定の日付範囲内の日付を正しく変換できない場合は、アプリケーションでこれを行うことがあります。 Windows XP のレジストリのタイム ゾーン データでは、通常、Windows Vista のレジストリで定義されているタイム ゾーンは 2 つの調整規則の情報を提供します、単一の調整規則をサポートしています。 これは、過去の時刻の変換が不正確であることを意味します。 シリアル化とタイム ゾーンのデータの逆シリアル化は、この制限を処理できます。

次の例では、カスタム<xref:System.TimeZoneInfo>を表す、米国の調整規則がないクラスが定義されています。東部標準時のゾーンは 1883 1917、米国で夏時間が登場する前にします。 カスタムのタイム ゾーンは、グローバル スコープを持つ変数にシリアル化されます。 タイム ゾーン変換メソッド`ConvertUtcTime`は、協定世界協定世界時 (UTC) 時刻が変換に渡されます。 日付と時刻は、1917年またはそれ以前に発生する場合、カスタム東部標準時ゾーンはシリアル化された文字列から復元され、レジストリから取得するタイム ゾーンが置き換えられます。

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>タイム ゾーンの例外の処理

レジストリは、動的な構造であるために、その内容は、偶発的または意図的な変更が適用されます。 つまり、レジストリで定義されていると、正常に実行するアプリケーションに必要なタイム ゾーンを指定しなくてもかまいません。 タイム ゾーンのシリアル化および逆シリアル化、サポートされていない場合、その結果を処理するが、ほとんどの選択肢がある<xref:System.TimeZoneNotFoundException>によってアプリケーションが終了します。 ただし、タイム ゾーンのシリアル化および逆シリアル化を使用して処理できます予期しない<xref:System.TimeZoneNotFoundException>復元することによって、シリアル化された文字列と、アプリケーションから必要なタイム ゾーンは引き続き実行します。

次の例では、作成し、カスタムの中部標準時ゾーンのシリアル化します。 レジストリから中部標準時ゾーンの取得が試行されます。 取得操作では、いずれかがスローした場合、<xref:System.TimeZoneNotFoundException>または<xref:System.InvalidTimeZoneException>、例外ハンドラーには、タイム ゾーンが逆シリアル化します。

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>シリアル化された文字列を保存して、必要なときに復元します。

前の例では、タイム ゾーン情報を文字列変数を格納し、必要なときに復元します。 ただし、シリアル化された時刻がゾーンの情報自体に格納できる外部ファイル、リソース ファイルなど、いくつかのストレージ メディアを格納する文字列は、アプリケーション、またはレジストリに埋め込まれます。 (カスタムのタイム ゾーンに関する情報がレジストリで、システムのタイム ゾーンのキーとは別に格納することに注意してください)。

この方法でシリアル化されたタイム ゾーン文字列を格納すると、タイム ゾーンの作成のルーチンも、アプリケーション自体とは別になります。 たとえば、タイム ゾーンの作成ルーチンは、実行し、アプリケーションが使用できる過去のタイム ゾーン情報を含むデータ ファイルを作成します。 データ ファイルを指定できます、アプリケーションと共にインストールして開くことができ、1 つまたは複数のタイム ゾーンのことが逆シリアル化、アプリケーションで必要なときにします。

タイム ゾーンのシリアル化されたデータの格納に埋め込みリソースを使用する例を参照してください。[方法。埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)と[方法。埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)します。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
