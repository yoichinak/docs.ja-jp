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
ms.openlocfilehash: c67a97193d186275e6a788f6b18bbc17c535f367
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912705"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>方法: 埋め込みリソースにタイム ゾーンを保存する

多くの場合、タイム ゾーンに対応するアプリケーションでは、特定のタイム ゾーンの存在が必要です。 ただし、ため、個々 の可用性<xref:System.TimeZoneInfo>オブジェクトは、システムのローカル レジストリに格納されている情報によって異なります、慣例的でも使用可能なタイム ゾーンが存在しない可能性があります。 使用してさらに、カスタム タイム ゾーンに関する情報がインスタンス化、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドは、レジストリ内の他のタイム ゾーン情報には格納されません。 必要なときにこれらのタイム ゾーンが使用できることを確認するには、シリアル化して保存し、それらを逆シリアル化して復元することができます。

通常、シリアル化、<xref:System.TimeZoneInfo>オブジェクトは、タイム ゾーン対応アプリケーションとは別に発生します。 シリアル化された保持するために使用されるデータ ストアによって<xref:System.TimeZoneInfo>オブジェクト、または (たとえば、レジストリのアプリケーション キーでデータが格納されている場合)、セットアップやインストール ルーチンの一部として実行しているユーティリティ ルーチンの一部としては、タイム ゾーンのデータをシリアル化される可能性があります前に、(たとえば、シリアル化されたデータは .NET XML リソース (.resx) ファイルに格納されている) 場合、最終的なアプリケーションがコンパイルされます。

だけでなく、アプリケーションでコンパイルされるリソース ファイル、その他のいくつかのデータ ストアは、タイム ゾーン情報を使用できます。 次に例を示します。

* レジストリ。 アプリケーションで、hkey_local_machine \software\microsoft\windows nt \currentversion\time Zones のサブキーを使用するのではなく、カスタムのタイム ゾーンのデータを格納する独自のアプリケーション キーのサブキーを使用することに注意してください。

* 構成ファイル。

* その他のシステム ファイル。

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>.Resx ファイルにシリアル化され、タイム ゾーンを保存するには

1. 既存のタイム ゾーンを取得するか、新しいタイム ゾーンを作成します。

   既存のタイム ゾーンを取得するには、次を参照してください。[方法。定義済みの UTC とローカル タイム ゾーン オブジェクトにアクセス](../../../docs/standard/datetime/access-utc-and-local.md)と[方法。TimeZoneInfo オブジェクトをインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)します。

   新しいタイム ゾーンを作成するには、いずれかのオーバー ロードを呼び出す、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッド。 詳細については、「[方法 :調整規則のないタイム ゾーンを作成](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)と[方法。タイム ゾーン調整規則を作成](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)です。

2. 呼び出す、<xref:System.TimeZoneInfo.ToSerializedString%2A>タイム ゾーンのデータを格納する文字列を作成します。

3. インスタンスを作成、<xref:System.IO.StreamWriter>オブジェクト、名前と必要に応じて、.resx ファイルのパスを提供することで、<xref:System.IO.StreamWriter>クラスのコンス トラクター。

4. インスタンスを作成、<xref:System.Resources.ResXResourceWriter>オブジェクトを渡すことによって、<xref:System.IO.StreamWriter>オブジェクトを<xref:System.Resources.ResXResourceWriter>クラスのコンス トラクター。

5. タイム ゾーンをパスに文字列をシリアル化、<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>メソッド。

6.  <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> メソッドを呼び出します。

7.  <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> メソッドを呼び出します。

8. 閉じる、<xref:System.IO.StreamWriter>オブジェクトを呼び出すことによってその<xref:System.IO.StreamWriter.Close%2A>メソッド。

9. アプリケーションの Visual Studio プロジェクトに生成された .resx ファイルを追加します。

10. 使用して、**プロパティ**Visual Studio で、ウィンドウを確認する、.resx ファイルの**ビルド アクション**プロパティに設定されて**埋め込まれたリソース**します。

## <a name="example"></a>例

次の例では、シリアル化、<xref:System.TimeZoneInfo>中部標準時を表すオブジェクトを<xref:System.TimeZoneInfo>SerializedTimeZones.resx という .NET XML リソース ファイルにパーマー基地、南極時間を表すオブジェクト。 中部標準時は通常、レジストリで定義されています。Palmer ステーション、南極カスタム タイム ゾーンです。

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

この例のシリアル化<xref:System.TimeZoneInfo>されるので使用可能なリソース ファイルのコンパイル時のオブジェクトします。

<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>メソッドは、.NET XML リソース ファイルに完全なヘッダー情報を追加、既存のファイルにリソースを追加するために使用できません。 例では、これを処理 SerializedTimeZones.resx ファイルをチェックして、存在する場合以外のすべてのリソースを格納する、2 つシリアル化をジェネリックのタイム ゾーン<xref:System.Collections.Generic.Dictionary%602>オブジェクト。 既存のファイルが削除され、既存のリソースが SerializedTimeZones.resx の新しいファイルに追加されます。 タイム ゾーンのシリアル化されたデータは、このファイルにも追加されます。

キー (または**名前**) リソースのフィールドは空白を含めることはできません。 <xref:System.String.Replace%28System.String%2CSystem.String%29>リソース ファイルに割り当てられている、前に、タイム ゾーン識別子のすべての埋め込みスペースを削除するメソッドが呼び出されます。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* System.Windows.Forms.dll、System.Core.dll への参照をプロジェクトに追加します。

* 次の名前空間は、インポートします。

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
- [方法: 埋め込みリソースからタイム ゾーンを復元します。](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
