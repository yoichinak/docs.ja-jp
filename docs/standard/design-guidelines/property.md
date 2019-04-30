---
title: プロパティのデザイン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: KrzysztofCwalina
ms.openlocfilehash: e4ed4fd39a9ebd63b9d5dbff38dc15647d65934f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026311"
---
# <a name="property-design"></a>プロパティのデザイン
プロパティはメソッドに厳密にはよく似ていますは、使用シナリオの観点からはまったく異なります。 これらは、スマート フィールドとして認識する必要があります。 呼び出し元のフィールドの構文とメソッドの柔軟性があります。  
  
 **✓ DO** 呼び出し元が、プロパティの値を変更すべき場合取得専用のプロパティを作成します。  
  
 留意している場合の種類、プロパティが変更可能な参照型、プロパティが取得専用の場合でも、プロパティの値を変更できます。  
  
 **X DO NOT** 設定専用のプロパティまたはプロパティを get アクセス操作子よりも広範なアクセシビリティを持つ set アクセス操作子を提供します。  
  
 たとえば、パブリック セッターと保護された getter プロパティは使用しないでいます。  
  
 プロパティの get アクセス操作子を提供できない場合は、メソッドと機能を実装します。 メソッド名の開始を検討してください`Set`し、何が名前を付けているプロパティ。 たとえば、<xref:System.AppDomain>というメソッドを持ち`SetCachePath`と呼ばれる設定専用のプロパティではなく`CachePath`します。  
  
 **✓ DO** 既定の設定がセキュリティ ホールや重大な非効率的なコードで発生しないようにする、すべてのプロパティの既定値を指定します。  
  
 **✓ DO** 場合でも、この結果、オブジェクトの一時的な無効な状態で、任意の順序で設定するプロパティを許可します。  
  
 同じオブジェクトの他のプロパティの値が指定の 2 つ以上のプロパティをいくつかの値を 1 つのプロパティの無効になるポイントを相互に関連する一般的です。 このような場合、オブジェクトによって、相互に関連するプロパティをまとめて使用実際になるまで無効な状態に起因する例外を延期する必要があります。  
  
 **✓ DO** プロパティ set アクセス操作子は例外をスローする場合は、以前の値を保持します。  
  
 **X AVOID** プロパティ get アクセス操作子から例外をスローします。  
  
 プロパティの getter は、単純な操作をする必要があり、すべての前提条件はありません。 Getter は、例外をスローできます、メソッドに設計おそらく必要があります。 このルールが、引数の検証の結果として例外を予定はインデクサーに適用されないことに注意してください。  
  
### <a name="indexed-property-design"></a>インデックス付きプロパティのデザイン  
 インデックス付きプロパティは、パラメーターを持つことができますし、配列のインデックスのような特別な構文で呼び出せる特別なプロパティです。  
  
 インデックス付きプロパティは、インデクサーとも呼ばれます。 インデクサーは、論理コレクション内の項目へのアクセスを提供する Api でのみ使用する必要があります。 たとえば、文字列は、一連の文字、およびインデクサーを<xref:System.String?displayProperty=nameWithType>その文字にアクセスするようになりました。  
  
 **✓ CONSIDER** 内部配列に格納されたデータへのアクセスを提供するインデクサーを使用します。  
  
 **✓ CONSIDER** 項目のコレクションを表す型のインデクサーを提供します。  
  
 **X AVOID** 1 つ以上のパラメーターを持つプロパティを使用してインデックスを作成します。  
  
 設計には、複数のパラメーターが必要とする場合は、プロパティは本当に論理的なコレクションにアクセサーを表すかどうかを再確認します。 そうでない場合は、代わりにメソッドを使用します。 メソッド名の開始を検討してください`Get`または`Set`します。  
  
 **X AVOID** 以外のパラメーターの型を持つインデクサー <xref:System.Int32?displayProperty=nameWithType>、 <xref:System.Int64?displayProperty=nameWithType>、 <xref:System.String?displayProperty=nameWithType>、 <xref:System.Object?displayProperty=nameWithType>、または列挙型。  
  
 設計には、他の種類のパラメーターが必要とする場合は、厳密に API が論理的なコレクションに実際にアクセサーを表すかどうかを再評価します。 そうでない場合は、メソッドを使用します。 メソッド名の開始を検討してください`Get`または`Set`します。  
  
 **✓ DO** 名前を使用して`Item`の言うまでもなく、名前がある場合を除き、インデックス付きプロパティ (などを参照してください、<xref:System.String.Chars%2A>プロパティを`System.String`)。  
  
 C# では、インデクサーは、既定の項目の名前は。 <xref:System.Runtime.CompilerServices.IndexerNameAttribute>この名前をカスタマイズするために使用できます。  
  
 **X DO NOT** インデクサーと意味的に等しいメソッドの両方を提供します。  
  
 **X DO NOT** 1 つの型でのオーバー ロードされたインデクサーの 1 つ以上のファミリを指定します。  
  
 これは、c# コンパイラによって強制されます。  
  
 **X DO NOT** 使用する既定以外のインデックス付きプロパティです。  
  
 これは、c# コンパイラによって強制されます。  
  
### <a name="property-change-notification-events"></a>プロパティ変更通知イベント  
 プロパティ値の変更のユーザーに通知するイベントを提供する便利な場合があります。 たとえば、`System.Windows.Forms.Control`を発生させます、`TextChanged`イベントの値の後にその`Text`プロパティが変更されました。  
  
 **✓ CONSIDER** 大まかな Api (通常、デザイナー コンポーネント) のプロパティ値が変更されたときに通知イベントを変更させるとします。  
  
 ユーザーがオブジェクトのプロパティを変更する場合を判断するに適したシナリオがある場合、オブジェクトは、プロパティの変更通知イベントを発生させます。  
  
 ただし、オーバーヘッドの基本型やコレクションなどの低レベルの Api のようなイベントを発生させるのには価値がある可能性がありますはありません。 たとえば、<xref:System.Collections.Generic.List%601>一覧に新しい項目が追加されたときに、このようなイベントが発生しないと、`Count`プロパティの変更。  
  
 **✓ CONSIDER** 外的要因を使用して、プロパティの値が変更されたときに、通知イベントを発生させる変更します。  
  
 いくつかの外的要因 (オブジェクトのメソッドを呼び出して、以外の方法) で使用してプロパティ値が変更された場合に発生させる値が変更され、変更されたことを開発者イベントを示します。 その良い例が、`Text`テキスト ボックス コントロールのプロパティ。 ユーザーがテキストで、`TextBox`プロパティの値が自動的に変更します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
