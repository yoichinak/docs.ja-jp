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
ms.openlocfilehash: 11f62b8fe8a28d6fe6401d53dac4b9bc1c45b21d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669109"
---
# <a name="instantiating-a-datetimeoffset-object"></a>DateTimeOffset オブジェクトのインスタンス化

<xref:System.DateTimeOffset>構造は新しいを作成する方法のいくつかあります<xref:System.DateTimeOffset>値。 新しくインスタンス化するために使用可能なメソッドに直接対応してそれらの多く<xref:System.DateTime>が強化された日付と時刻の値には世界協定時刻 (UTC) からのオフセットを指定するための値。 具体的には、インスタンス化できる、<xref:System.DateTimeOffset>次の方法で値。

* 日付と時刻のリテラルを使用します。

* 呼び出すことによって、<xref:System.DateTimeOffset>コンス トラクター。

* 値を暗黙的に変換することで<xref:System.DateTimeOffset>値。

* 日付と時刻の文字列形式を解析する。

このトピックでは新しいをインスタンス化したこれらのメソッドを示す詳細とコードの大きい例<xref:System.DateTimeOffset>値。

## <a name="date-and-time-literals"></a>日付と時刻のリテラル

インスタンス化する最も一般的な方法の 1 つをサポートする言語を<xref:System.DateTime>値は日付と時刻をハード コーディングされたリテラル値としてを提供します。 たとえば、次の Visual Basic コードの作成、<xref:System.DateTime>オブジェクトの値を持つは 2008 年 1 月 1 日午前 10時 00分です。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> サポートする言語を使用する場合は、日付と時刻のリテラルを使用して値を初期化することも<xref:System.DateTime>リテラル。 たとえば、次の Visual Basic コードの作成、<xref:System.DateTimeOffset>オブジェクト。

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

コンソール出力に示すよう、<xref:System.DateTimeOffset>この方法で作成された値には、ローカル タイム ゾーンのオフセットが割り当てられます。 つまり、<xref:System.DateTimeOffset>コードが別のコンピューターで実行された場合、リテラル文字を使用して割り当てられた値が 1 つの特定の時点を識別できません。

## <a name="datetimeoffset-constructors"></a>DateTimeOffset コンス トラクター

<xref:System.DateTimeOffset>型は、6 つのコンス トラクターを定義します。 直接対応しているうちの 4 つ<xref:System.DateTime>コンス トラクターの型のパラメーターを追加、<xref:System.TimeSpan>日付を定義して、時間を UTC からのオフセットします。 定義することはこれらを<xref:System.DateTimeOffset>値の個々 の日付と時刻のコンポーネントの値に基づいています。 次のコードはこれら 4 つのコンス トラクターを使用して、インスタンス化するなど、 <xref:System.DateTimeOffset> 2008 年 7 月 1 の同じ値を持つオブジェクト 12時 05分 AM +01: 00 です。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

なお、ときの値、<xref:System.DateTimeOffset>オブジェクトを使用してインスタンス化、<xref:System.Globalization.PersianCalendar>として、コンス トラクターに引数の 1 つのオブジェクトがコンソールに表示、ペルシャ暦ではなく、グレゴリオ暦の日付として表されます。 ペルシャ暦で日付を出力する例を参照してください、<xref:System.Globalization.PersianCalendar>トピック。

その他の 2 つのコンス トラクターを作成、<xref:System.DateTimeOffset>オブジェクトから、<xref:System.DateTime>値。 最初の 1 つのパラメーターを持つ、<xref:System.DateTime>に変換する値を<xref:System.DateTimeOffset>値。 結果のオフセット<xref:System.DateTimeOffset>値によって異なります、<xref:System.DateTime.Kind%2A>コンス トラクターの 1 つのパラメーターのプロパティ。 値が場合<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>、オフセットと等しい設定<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 それ以外の場合、オフセットはローカル タイム ゾーンのオフセットと等しい値に設定されます。 次の例は、インスタンスを作成するこのコンス トラクターの使用を示します<xref:System.DateTimeOffset>UTC とローカル タイム ゾーンを表すオブジェクト。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> オーバー ロードを呼び出し、<xref:System.DateTimeOffset>を 1 つを持つコンス トラクター<xref:System.DateTime>パラメーターの暗黙の変換を実行するのには、<xref:System.DateTime>値を<xref:System.DateTimeOffset>値。

作成する 2 つ目のコンス トラクター、<xref:System.DateTimeOffset>オブジェクトから、<xref:System.DateTime>値が 2 つのパラメーター:<xref:System.DateTime>変換対象の値と<xref:System.TimeSpan>日付と時刻を表す値を UTC からのオフセットします。 このオフセット値に対応する必要があります、<xref:System.DateTime.Kind%2A>コンス トラクターの最初のパラメーターのプロパティまたは<xref:System.ArgumentException>がスローされます。 場合、<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティが<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>、2 番目のパラメーターの値である必要があります<xref:System.TimeSpan.Zero?displayProperty=nameWithType>します。 場合、<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティが<xref:System.DateTimeKind.Local?displayProperty=nameWithType>、2 番目のパラメーターの値はローカル システムのタイム ゾーンのオフセットである必要があります。 場合、<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティが<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>オフセットが有効な値を指定できます。 次のコードはこのコンス トラクターの呼び出しに変換する<xref:System.DateTime>に<xref:System.DateTimeOffset>値。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>暗黙的な型変換

<xref:System.DateTimeOffset>型は、1 つの暗黙的な型変換をサポートしています: から、<xref:System.DateTime>値を<xref:System.DateTimeOffset>値。 (暗黙的な型変換とは、明示的なキャスト (C# の場合) または変換 (Visual Basic の場合) を必要とせず、情報を失わない 1 つの型から別の型への変換です)。 これにより、次のようなコードが可能となります。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

結果のオフセット<xref:System.DateTimeOffset>値によって異なります、<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティの値。 値が場合<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>、オフセットと等しい設定<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。 いずれかの値が場合<xref:System.DateTimeKind.Local?displayProperty=nameWithType>または<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>オフセットは、ローカル タイム ゾーンのと同じに設定されます。

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>日付と時刻の文字列形式の解析

<xref:System.DateTimeOffset>に日時、日付の文字列形式に変換するための 4 つのメソッドをサポートする型、<xref:System.DateTimeOffset>値。

* <xref:System.DateTimeOffset.Parse%2A>、日付の文字列形式を変換する日時をしようとする、<xref:System.DateTimeOffset>値し、変換が失敗した場合に例外をスローします。

* <xref:System.DateTimeOffset.TryParse%2A>、日付の文字列形式を変換する日時をしようとする、<xref:System.DateTimeOffset>値を返します`false`変換が失敗した場合。

* <xref:System.DateTimeOffset.ParseExact%2A>、日付と時刻を指定した形式の文字列形式に変換しようと試みます、<xref:System.DateTimeOffset>値。 変換が失敗すると、メソッドは例外をスローします。

* <xref:System.DateTimeOffset.TryParseExact%2A>、日付と時刻を指定した形式の文字列形式に変換しようと試みます、<xref:System.DateTimeOffset>値。 変換が失敗すると、メソッドは `false` を返します。

次の例では、これらの 4 つの文字列変換メソッドの各インスタンス化への呼び出しを<xref:System.DateTimeOffset>値。

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
