---
title: '方法: 埋め込みリソースからタイム ゾーンを復元する'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98813bf6685be78d33ebd5cc5e8c07a61a811c25
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106760"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>方法: 埋め込みリソースからタイム ゾーンを復元する

このトピックでは、リソースファイルに保存されているタイムゾーンを復元する方法について説明します。 タイムゾーンの保存に関する情報および手順に[ついては、「方法:埋め込みリソース](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)にタイムゾーンを保存します。

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>埋め込みリソースから TimeZoneInfo オブジェクトを逆シリアル化するには

1. 取得するタイムゾーンがカスタムタイムゾーンでない場合は、 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>メソッドを使用してインスタンス化します。

2. 埋め込み<xref:System.Resources.ResourceManager>リソースファイルの完全修飾名と、リソースファイルを含むアセンブリへの参照を渡すことによって、オブジェクトをインスタンス化します。

   埋め込まれたリソースファイルの完全修飾名を特定できない場合は、 [ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)を使用して、アセンブリのマニフェストを確認します。 リソース`.mresource`を識別するエントリ。 この例では、リソースの完全修飾名は`SerializeTimeZoneData.SerializedTimeZones`です。

   リソースファイルが、タイムゾーンのインスタンス化コードを含む同じアセンブリに埋め込まれている場合は、 `static` (`Shared` Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A>メソッドを呼び出すことによって、そのファイルへの参照を取得できます。

3. メソッドの<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>呼び出しが失敗した場合、またはカスタムタイムゾーンをインスタンス化する場合は、 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>メソッドを呼び出して、シリアル化されたタイムゾーンを含む文字列を取得します。

4. <xref:System.TimeZoneInfo.FromSerializedString%2A>メソッドを呼び出してタイムゾーンデータを逆シリアル化します。

## <a name="example"></a>例

次の例では<xref:System.TimeZoneInfo> 、埋め込み .net XML リソースファイルに格納されているオブジェクトを逆シリアル化します。

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

このコードは、アプリケーションに必要な<xref:System.TimeZoneInfo>オブジェクトが存在することを確認するための例外処理を示しています。 まず、 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>メソッドを使用し<xref:System.TimeZoneInfo>てレジストリからオブジェクトを取得することによって、オブジェクトのインスタンス化を試みます。 タイムゾーンをインスタンス化できない場合、コードは埋め込みリソースファイルからタイムゾーンを取得します。

カスタムタイムゾーン ( <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドを使用してインスタンス化されたタイムゾーン) のデータはレジストリに格納されないため、コードはを呼び出して、 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>南極のタイムゾーンをインスタンス化しません。 代わりに、埋め込みリソースファイルをすぐに検索して、 <xref:System.TimeZoneInfo.FromSerializedString%2A>メソッドを呼び出す前にタイムゾーンのデータを含む文字列を取得します。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- このプロジェクトには、System. .dll と system.servicemodel への参照を追加する必要があります。

- 次の名前空間がインポートされます。

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
- [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
- [方法: 埋め込みリソースにタイムゾーンを保存する](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
