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
ms.openlocfilehash: f9fe3045d8bd8b4d625c5cd49bc18574ebb740de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026433"
---
# <a name="exceptions-and-performance"></a>例外とパフォーマンス
例外に関連する一般的な懸念事項の 1 つを定期的に失敗したコードの例外を使用している場合、パフォーマンスの実装は受け入れられない。 これはもっともです。 メンバーは、例外をスローするときに、パフォーマンスが極端に遅くにできます。 ただし、エラー コードの使用を禁止する例外のガイドラインに厳密に準拠しつつ、良好なパフォーマンスを実現することができます。 このセクションで説明されている 2 つのパターンは、これを行う方法をお勧めします。  
  
 **X DO NOT** 例外がパフォーマンスに悪影響を及ぼす影響する問題が原因のエラー コードを使用します。  
  
 パフォーマンスを向上させるのには、Tester-doer パターンまたは解析を試行パターンは、次の 2 つのセクションで説明されているかを使用して、します。  
  
## <a name="tester-doer-pattern"></a>Tester-doer パターン  
 場合があります、メンバーを 2 つに分割することにより、例外のスローのメンバーのパフォーマンスが向上することができます。 見て、<xref:System.Collections.Generic.ICollection%601.Add%2A>のメソッド、<xref:System.Collections.Generic.ICollection%601>インターフェイス。  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 メソッド`Add`コレクションが読み取り専用の場合にスローします。 これは、メソッドの呼び出しが失敗する多くの場合に必要な場合のシナリオでパフォーマンスの問題です。 値を追加する前に、コレクションが書き込み可能かどうかをテストすると、問題を軽減する方法のいずれかです。  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 この例では、プロパティを条件をテストするために使用するメンバー `IsReadOnly`、テスト担当者と呼びます。 スロー可能性のある操作を実行するために使用するメンバー、`Add`例では、メソッドは、渡ってと呼ばれます。  
  
 **✓ CONSIDER** Tester 渡ってパターンが例外をスローするメンバーの共通のパフォーマンスの問題を回避するシナリオに関連する例外。  
  
## <a name="try-parse-pattern"></a>解析を試行パターン  
 非常にパフォーマンスが重視される api の場合は、前のセクションで説明されている Tester-doer パターンよりもさらに高速のパターンを使用してください。 メンバーのセマンティクスの一部の場合、適切に定義されたテストを作成するメンバーの名前を調整するためのパターンを呼び出します。 たとえば、<xref:System.DateTime>定義、<xref:System.DateTime.Parse%2A>文字列の解析に失敗した場合に例外をスローするメソッド。 対応する定義も<xref:System.DateTime.TryParse%2A>を解析しようとするメソッドが false を返します解析が失敗し、正常に解析を使用して、結果を返す場合、`out`パラメーター。  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 このパターンを使用する場合は、厳密な用語でお試しください機能を定義する必要があります。 メンバーに適切に定義された try 以外の何らかの理由で失敗した場合、メンバーが対応する例外をスローする必要があります。  
  
 **✓ CONSIDER** Try 解析パターンが例外をスローするメンバーの共通のパフォーマンスの問題を回避するシナリオに関連する例外。  
  
 **✓ DO** このパターンを実装するメソッドにプレフィックス"Try"とブール型の戻り値の型を使用します。  
  
 **✓ DO** Try 解析パターンを使用する各メンバーに対して例外スローのメンバーを提供します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)
