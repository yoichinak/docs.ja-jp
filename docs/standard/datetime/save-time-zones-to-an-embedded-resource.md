---
title: '方法: 埋め込みリソースにタイム ゾーンを保存する'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ca39d989cc7bc16ec2678ba5fa53710899f3ac4
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107155"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>方法: 埋め込みリソースにタイム ゾーンを保存する

タイムゾーンに対応するアプリケーションでは、多くの場合、特定のタイムゾーンが存在する必要があります。 ただし、個々<xref:System.TimeZoneInfo>のオブジェクトの可用性は、ローカルシステムのレジストリに格納されている情報によって異なるため、通常使用可能なタイムゾーンも存在しない可能性があります。 また、 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドを使用してインスタンス化されたカスタムタイムゾーンに関する情報は、他のタイムゾーン情報と共にレジストリに格納されるわけではありません。 これらのタイムゾーンが必要なときに確実に使用できるようにするには、それらをシリアル化して保存し、後でそれらを逆シリアル化して復元します。

通常、オブジェクトの<xref:System.TimeZoneInfo>シリアル化は、タイムゾーン対応アプリケーションとは別に行われます。 シリアル化<xref:System.TimeZoneInfo>されたオブジェクトを保持するために使用されるデータストアによっては、タイムゾーンデータがセットアップまたはインストールルーチンの一部としてシリアル化されることがあります (たとえば、データがレジストリのアプリケーションキーに格納されている場合)。または、を実行するユーティリティルーチンの一部として、最終的なアプリケーションをコンパイルする前 (たとえば、.NET XML リソース (.resx) ファイルにシリアル化されたデータを格納する場合)。

アプリケーションと共にコンパイルされるリソースファイルに加えて、他のいくつかのデータストアをタイムゾーン情報に使用できます。 次に例を示します。

- レジストリ。 アプリケーションでは、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones のサブキーを使用するのではなく、独自のアプリケーションキーのサブキーを使用して、カスタムタイムゾーンデータを格納する必要があることに注意してください。

- 構成ファイル。

- その他のシステムファイル。

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>.Resx ファイルにシリアル化してタイムゾーンを保存するには

1. 既存のタイムゾーンを取得するか、新しいタイムゾーンを作成します。

   既存のタイムゾーンを取得するに[は、「方法:定義済みの UTC およびローカルタイムゾーンオブジェクト](../../../docs/standard/datetime/access-utc-and-local.md)に[アクセスし、次の操作を行います。TimeZoneInfo オブジェクト](../../../docs/standard/datetime/instantiate-time-zone-info.md)をインスタンス化します。

   新しいタイムゾーンを作成するには、 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドのいずれかのオーバーロードを呼び出します。 詳細については、「[方法 :調整規則](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)のないタイムゾーンを[作成し、次の操作を行います。調整規則](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)のあるタイムゾーンを作成します。

2. <xref:System.TimeZoneInfo.ToSerializedString%2A>メソッドを呼び出して、タイムゾーンのデータを含む文字列を作成します。

3. 名前を<xref:System.IO.StreamWriter>指定し、必要に応じて<xref:System.IO.StreamWriter>クラスコンストラクターに .resx ファイルのパスを指定して、オブジェクトをインスタンス化します。

4. オブジェクトを<xref:System.Resources.ResXResourceWriter> <xref:System.Resources.ResXResourceWriter>クラスコンストラクターに<xref:System.IO.StreamWriter>渡すことによって、オブジェクトをインスタンス化します。

5. タイムゾーンのシリアル化された文字列<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>をメソッドに渡します。

6. <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> メソッドを呼び出します。

7. <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> メソッドを呼び出します。

8. メソッド<xref:System.IO.StreamWriter.Close%2A>を<xref:System.IO.StreamWriter>呼び出して、オブジェクトを閉じます。

9. 生成された .resx ファイルをアプリケーションの Visual Studio プロジェクトに追加します。

10. Visual Studio の **[プロパティ]** ウィンドウを使用して、.resx ファイルの **[ビルドアクション]** プロパティが **[埋め込みリソース]** に設定されていることを確認します。

## <a name="example"></a>例

次の例では<xref:System.TimeZoneInfo> 、中部標準時<xref:System.TimeZoneInfo>を表すオブジェクトをシリアル化し、SerializedTimeZones という名前の .net XML リソースファイルの南極 Time を表すオブジェクトをシリアル化します。 通常、中部標準時はレジストリで定義されています。パーマーステーション、南極はカスタムタイムゾーンです。

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

この例で<xref:System.TimeZoneInfo>は、コンパイル時にリソースファイルで使用できるようにオブジェクトをシリアル化します。

メソッドは<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 、完全なヘッダー情報を .net XML リソースファイルに追加するため、既存のファイルにリソースを追加するために使用することはできません。 この例では、SerializedTimeZones ファイルを確認し、存在する場合は、2つのシリアル化されたタイムゾーン以外のすべてのリソースを汎用<xref:System.Collections.Generic.Dictionary%602>オブジェクトに格納することで、この処理を行います。 その後、既存のファイルが削除され、既存のリソースが新しい SerializedTimeZones ファイルに追加されます。 シリアル化されたタイムゾーンデータもこのファイルに追加されます。

リソースのキー (または**名前**) フィールドには、空白を埋め込むことはできません。 メソッド<xref:System.String.Replace%28System.String%2CSystem.String%29>は、リソースファイルに割り当てられる前に、タイムゾーン識別子内のすべての埋め込みスペースを削除するために呼び出されます。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- このプロジェクトには、System. .dll と system.servicemodel への参照を追加する必要があります。

- 次の名前空間がインポートされます。

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
- [方法: 埋め込みリソースからタイムゾーンを復元する](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
