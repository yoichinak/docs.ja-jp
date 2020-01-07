---
title: Extension のメソッド
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: KrzysztofCwalina
ms.openlocfilehash: ad78bae2dc7a3000b67224da6f1a8c578053087f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347028"
---
# <a name="extension-methods"></a>Extension のメソッド
拡張メソッドは、インスタンスメソッド呼び出し構文を使用して静的メソッドを呼び出せるようにする言語機能です。 これらのメソッドは、メソッドが操作するインスタンスを表す1つ以上のパラメーターを受け取る必要があります。  
  
 このような拡張メソッドを定義するクラスは "スポンサー" クラスと呼ばれ、static として宣言する必要があります。 拡張メソッドを使用するには、スポンサークラスを定義する名前空間をインポートする必要があります。  
  
 **X AVOID** いないこと、お持ちでない型に特に拡張メソッドを定義します。  
  
 型のソースコードを所有している場合は、代わりに通常のインスタンスメソッドを使用することを検討してください。 を所有しておらず、メソッドを追加する場合は、細心の注意を払ってください。 拡張メソッドを自由に使用すると、これらのメソッドを使用するように設計されていない型の Api が乱雑になる可能性があります。  
  
 **✓ CONSIDER** 拡張メソッドを使用して、次のシナリオのいずれかで。  
  
- インターフェイスのすべての実装に関連するヘルパー機能を提供するために、がコアインターフェイスの観点で記述されている場合は、この機能を使用できます。 これは、具象実装がインターフェイスに割り当てられないことが原因です。 たとえば、`LINQ to Objects` の演算子は、すべての <xref:System.Collections.Generic.IEnumerable%601> 型の拡張メソッドとして実装されます。 したがって、`IEnumerable<>` の実装はすべて自動的に LINQ 対応になります。  
  
- インスタンスメソッドで何らかの種類の依存関係が発生しても、そのような依存関係は依存関係管理規則に違反する可能性があります。 たとえば、<xref:System.String> から <xref:System.Uri?displayProperty=nameWithType> への依存関係はおそらく望ましくありません。 `String.ToUri()` そのため `System.Uri` を返すインスタンスメソッドは、依存関係管理の観点からは不適切な設計になります。 `System.Uri` を返す静的な拡張メソッドは、より優れたデザインであることが `Uri.ToUri(this string str)` ます。  
  
 **X AVOID** で拡張メソッドを定義する<xref:System.Object?displayProperty=nameWithType>です。  
  
 Visual Basic ユーザーは、拡張メソッドの構文を使用して、オブジェクト参照に対してこのようなメソッドを呼び出すことはできません。 Visual Basic は、このようなメソッドの呼び出しをサポートしていません。これは、Visual Basic では、参照をオブジェクトとして宣言すると、すべてのメソッドの呼び出しが遅延バインディングされる (実際のメンバーは実行時に決定される) のに対し、拡張メソッドへのバインディングはで決定されるためです。コンパイル時 (事前バインディング)。  
  
 ガイドラインは、同じバインディング動作が存在する他の言語、または拡張メソッドがサポートされていない他の言語に適用されることに注意してください。  
  
 **X DO NOT** インターフェイスにメソッドを追加または依存関係の管理用である場合を除き、拡張の型と同じ名前空間の拡張メソッドを格納します。  
  
 **X AVOID** 異なる名前空間にある場合でも、同じシグネチャを持つ 2 つ以上の拡張メソッドを定義します。  
  
 **✓ CONSIDER** 型がインターフェイスで、ほとんどまたはすべてのケースで使用する拡張メソッドは、拡張された型と同じ名前空間に拡張メソッドを定義します。  
  
 **X DO NOT** 通常その他の機能に関連付けられている名前空間の機能を実装する拡張メソッドを定義します。 代わりに、所属する機能に関連付けられている名前空間で定義します。  
  
 **X AVOID** 拡張メソッド (たとえば、「拡張」) を専用の名前空間の汎用名前付けします。 代わりに、わかりやすい名前 ("Routing" など) を使用してください。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
