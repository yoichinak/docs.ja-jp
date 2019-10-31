---
title: 例外とパフォーマンス
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: KrzysztofCwalina
ms.openlocfilehash: 967692092186b81802a7ab635ea8fe4dbacd49ed
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611519"
---
# <a name="exceptions-and-performance"></a>例外とパフォーマンス
例外に関する一般的な懸念事項の1つとして、定期的に失敗するコードに例外を使用すると、実装のパフォーマンスが許容されなくなることがあります。 これは有効な問題です。 メンバーが例外をスローすると、パフォーマンスが低下することがあります。 ただし、エラーコードの使用を禁止する例外ガイドラインに厳密に準拠しながら、パフォーマンスを向上させることができます。 このセクションで説明する2つのパターンは、この方法を示しています。

 **X DO NOT** 例外がパフォーマンスに悪影響を及ぼす影響する問題が原因のエラー コードを使用します。

 パフォーマンスを向上させるために、次の 2 つのセクションで説明するように、Tester-Doer パターンまたは Try-Parse パターンを使用することができます。

## <a name="tester-doer-pattern"></a>テスト担当者-Doer パターン
 メンバーを2つに分割すると、例外スローメンバーのパフォーマンスを向上させることができます。 では、 <xref:System.Collections.Generic.ICollection%601>インターフェイスの<xref:System.Collections.Generic.ICollection%601.Add%2A>メソッドを見てみましょう。

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 コレクションが読み取り専用の場合、`Add` メソッドは例外をスローします。 これは、メソッドの呼び出しが頻繁に失敗することが予想されるシナリオでパフォーマンスの問題になる可能性があります。 問題を軽減する方法の 1 つは、値を追加する前に、コレクションが書き込み可能かどうかをテストすることです。

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 条件をテストするために使用されるメンバー (この例では `IsReadOnly` プロパティ) は、tester と呼ばれています。 例外がスローされる可能性のある操作を実行するために使用するメンバー (この例では `Add` メソッド) は、doer と呼ばれています。

 **✓ CONSIDER** Tester 渡ってパターンが例外をスローするメンバーの共通のパフォーマンスの問題を回避するシナリオに関連する例外。

## <a name="try-parse-pattern"></a>Try 解析パターン
 パフォーマンスが非常に重要な API では、前のセクションで説明した Tester-Doer パターンよりも高速なパターンを使用する必要があります。 このパターンでは、メンバー名を調整して、適切に定義されたテスト ケースをメンバー セマンティクスの一部にするための呼び出しを行います。 たとえば、<xref:System.DateTime> は、文字列の解析が失敗した場合に例外をスローする <xref:System.DateTime.Parse%2A> メソッドを定義します。 また、解析を試行する対応する <xref:System.DateTime.TryParse%2A> メソッドも定義しますが、解析が失敗した場合は false を返し、`out` パラメーターを使用して解析の成功の結果を返します。

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 このパターンを使用する場合は、厳密な用語で try 機能を定義する必要があります。 明確に定義された try 以外の理由でメンバーが失敗した場合でも、メンバーは対応する例外をスローする必要があります。

 **✓ CONSIDER** 例外に関連するパフォーマンスの問題を回避するため、一般的なシナリオで例外をスローする可能性のあるメンバー向けに Try-Parse を検討します。

 **✓ DO** このパターンを実装するメソッドにプレフィックス"Try"とブール型の戻り値の型を使用します。

 **✓ DO** Try 解析パターンを使用する各メンバーに対して例外スローのメンバーを提供します。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *次のフレームワークの設計ガイドラインから[、ピアソン教育, inc. のアクセス許可によって再度ご説明します。Microsoft Windows 開発シリーズの一部として、Addison-Wesley](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Professional によって2008年10月22日公開された、再利用可能な .net ライブラリの Krzysztof Cwalina および Brad abrams の規則、表現、パターン。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)
