---
title: DateTimeOffset オブジェクトのインスタンス化
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50cc71b62581e1fb9302fe241abf6349afd33f8d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106644"
---
# <a name="instantiating-a-datetimeoffset-object"></a>DateTimeOffset オブジェクトのインスタンス化

構造<xref:System.DateTimeOffset>体には、新しい<xref:System.DateTimeOffset>値を作成するためのさまざまな方法が用意されています。 これらの多くは、新しい<xref:System.DateTime>値をインスタンス化するために使用できるメソッドに直接対応しています。拡張機能を使用すると、世界協定時刻 (UTC) からの日付と時刻の値のオフセットを指定できます。 特に、次の方法で<xref:System.DateTimeOffset>値をインスタンス化できます。

- 日付と時刻のリテラルを使用する。

- コンストラクターを<xref:System.DateTimeOffset>呼び出します。

- 値を値に暗黙的に<xref:System.DateTimeOffset>変換する。

- 日付と時刻の文字列形式を解析する。

このトピックでは、新しい<xref:System.DateTimeOffset>値をインスタンス化するこれらのメソッドを示す、より詳細なコード例を示します。

## <a name="date-and-time-literals"></a>日付と時刻のリテラル

これをサポートする言語では、値を<xref:System.DateTime>インスタンス化する最も一般的な方法の1つは、ハードコーディングされたリテラル値として日付と時刻を指定することです。 たとえば、次の Visual Basic コードでは、 <xref:System.DateTime> 10:00 AM で2008年1月1日の値を持つオブジェクトを作成します。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset>リテラルをサポート<xref:System.DateTime>する言語を使用する場合は、日付と時刻のリテラルを使用して値を初期化することもできます。 たとえば、次の Visual Basic コードはオブジェクトを<xref:System.DateTimeOffset>作成します。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

コンソール出力に示されている<xref:System.DateTimeOffset>ように、この方法で作成された値には、ローカルタイムゾーンのオフセットが割り当てられます。 つまり、コードが<xref:System.DateTimeOffset>別のコンピューターで実行されている場合、文字リテラルを使用して割り当てられた値は、単一の時点を識別しません。

## <a name="datetimeoffset-constructors"></a>DateTimeOffset コンストラクター

この<xref:System.DateTimeOffset>型は6つのコンストラクターを定義します。 これらの4つはコンストラクター <xref:System.DateTime>に直接対応しており、UTC <xref:System.TimeSpan>からの日付と時刻のオフセットを定義する型の追加パラメーターがあります。 これにより、個々の<xref:System.DateTimeOffset>日付と時刻のコンポーネントの値に基づいて値を定義できます。 たとえば、次のコードでは、これらの4つ<xref:System.DateTimeOffset>のコンストラクターを使用して、7/1/2008 12:05 AM + 01:00 と同じ値を持つオブジェクトをインスタンス化しています。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

オブジェクトをコンストラクターに渡す引数の 1 <xref:System.DateTimeOffset>つとして<xref:System.Globalization.PersianCalendar>使用してインスタンス化されたオブジェクトの値がコンソールに表示される場合は、ペルシャ暦ではなく、グレゴリオ暦の日付として表現されます。 ペルシャ暦を使用して日付を出力するには、 <xref:System.Globalization.PersianCalendar> 「」の例を参照してください。

他の2つのコンストラクター <xref:System.DateTimeOffset>は、 <xref:System.DateTime>値からオブジェクトを作成します。 最初のパラメーターには1つのパラメーターが<xref:System.DateTime>あり、値は<xref:System.DateTimeOffset>値に変換されます。 結果<xref:System.DateTimeOffset>の値のオフセットは、コンストラクターの<xref:System.DateTime.Kind%2A>単一のパラメーターのプロパティによって異なります。 値が<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>の場合、オフセットはに等しい値に<xref:System.TimeSpan.Zero?displayProperty=nameWithType>設定されます。 それ以外の場合、オフセットはローカル タイム ゾーンのオフセットと等しい値に設定されます。 次の例は、このコンストラクターを使用して<xref:System.DateTimeOffset> 、UTC とローカルタイムゾーンを表すオブジェクトをインスタンス化する方法を示しています。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> <xref:System.DateTimeOffset> 1 つ<xref:System.DateTime>のパラメーターを持つコンストラクターのオーバーロードを呼び出すことは、値から<xref:System.DateTimeOffset>値への<xref:System.DateTime>暗黙的な変換を実行することと同じです。

値からオブジェクトを<xref:System.DateTimeOffset>作成する2つ目のコンストラクター <xref:System.DateTime>には、変換する値と<xref:System.TimeSpan> UTC からの日付と時刻のオフセットを表す値の2つのパラメーターがあります。 <xref:System.DateTime> このオフセット値は、コンストラクターの<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティに対応して<xref:System.ArgumentException>いる必要があります。指定しないと、がスローされます。 最初のパラメーターの<xref:System.DateTimeKind.Utc?displayProperty=nameWithType> <xref:System.TimeSpan.Zero?displayProperty=nameWithType>プロパティがの場合、2番目のパラメーターの値はである必要があります。 <xref:System.DateTime.Kind%2A> 最初のパラメーターの<xref:System.DateTimeKind.Local?displayProperty=nameWithType>プロパティがの場合、2番目のパラメーターの値は、ローカルシステムのタイムゾーンのオフセットである必要があります。<xref:System.DateTime.Kind%2A> 最初のパラメーターの<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>プロパティがの場合、オフセットには任意の有効な値を指定できます。<xref:System.DateTime.Kind%2A> 次のコードは、値に<xref:System.DateTime> <xref:System.DateTimeOffset>変換するこのコンストラクターの呼び出しを示しています。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>暗黙の型変換

型<xref:System.DateTimeOffset>は、値から<xref:System.DateTimeOffset>値への暗黙的な<xref:System.DateTime>型変換を1つサポートします。 (暗黙的な型変換とは、明示的なキャスト (C# の場合) または変換 (Visual Basic の場合) を必要とせず、情報を失わない 1 つの型から別の型への変換です)。 これにより、次のようなコードが可能となります。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

結果<xref:System.DateTimeOffset>の値のオフセットは、 <xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティ値によって異なります。 値が<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>の場合、オフセットはに等しい値に<xref:System.TimeSpan.Zero?displayProperty=nameWithType>設定されます。 値が<xref:System.DateTimeKind.Local?displayProperty=nameWithType>または<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>の場合、オフセットはローカルタイムゾーンのオフセットと同じに設定されます。

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>日付と時刻の文字列形式の解析

型<xref:System.DateTimeOffset>では、日付と時刻の文字列形式を<xref:System.DateTimeOffset>値に変換できる4つのメソッドがサポートされています。

- <xref:System.DateTimeOffset.Parse%2A>。日付と時刻の文字列形式を<xref:System.DateTimeOffset>値に変換しようとし、変換に失敗した場合は例外をスローします。

- <xref:System.DateTimeOffset.TryParse%2A>。日付と時刻の文字列形式を<xref:System.DateTimeOffset>値に変換しようとし、変換に失敗した場合はを返し`false`ます。

- <xref:System.DateTimeOffset.ParseExact%2A>。指定した形式の日付と時刻の文字列形式を<xref:System.DateTimeOffset>値に変換しようとします。 変換が失敗すると、メソッドは例外をスローします。

- <xref:System.DateTimeOffset.TryParseExact%2A>。指定した形式の日付と時刻の文字列形式を<xref:System.DateTimeOffset>値に変換しようとします。 変換が失敗すると、メソッドは `false` を返します。

次の例では、これらの4つの文字列変換メソッドを呼び出し<xref:System.DateTimeOffset>て値をインスタンス化しています。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
