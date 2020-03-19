---
title: 演算子のオーバーロード
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401221"
---
# <a name="operator-overloads"></a>演算子のオーバーロード
演算子のオーバーロードを使用すると、フレームワークの型は組み込みの言語プリミティブのように見えます。

 許可され、役立つ場合もありますが、演算子のオーバーロードは慎重に使用する必要があります。 フレームワークの設計者が単純なメソッドである必要がある操作に演算子を使用し始めた場合など、演算子のオーバーロードが悪用されたケースが多くあります。 次のガイドラインは、演算子のオーバーロードを使用するタイミングと方法を決定する際に役立ちます。

 ❌プリミティブ (組み込み) 型のように感じる型を除き、演算子のオーバーロードを定義しないようにします。

 ✔️プリミティブ型のように感じる型で演算子のオーバーロードを定義することを検討してください。

 たとえば、<xref:System.String?displayProperty=nameWithType>を持`operator==`っていると`operator!=`定義されています。

 ✔️は、数値を表す構造体の演算子のオーバーロードを定義します<xref:System.Decimal?displayProperty=nameWithType>( など )。

 ❌演算子のオーバーロードを定義するときにかわいいしないでください。

 演算子のオーバーロードは、操作の結果が何であるかがすぐにわかる場合に便利です。 たとえば、互<xref:System.DateTime>`DateTime`いに減算して<xref:System.TimeSpan>. ただし、論理共用体演算子を使用して 2 つのデータベース照会を共用するか、シフト演算子を使用してストリームに書き込むのは適切ではありません。

 ❌少なくとも 1 つのオペランドがオーバーロードを定義する型でない限り、演算子のオーバーロードを提供しないでください。

 ✔️演算子を対称的にオーバーロードします。

 たとえば、`operator==`をオーバーロードする場合は、 もオーバーロードする`operator!=`必要があります。 同様に、`operator<`をオーバーロードする場合は、 など`operator>`もオーバーロードする必要があります。

 ✔️ CONSIDER オーバーロードされた各演算子に対応するフレンドリ名を持つメソッドを提供します。

 多くの言語では、演算子のオーバーロードはサポートされていません。 このため、演算子をオーバーロードする型には、同等の機能を提供する適切なドメイン固有の名前を持つセカンダリ メソッドを含める方法をお勧めします。

 次の表に、演算子と対応するフレンドリ メソッド名の一覧を示します。

|C# 演算子記号|メタデータ名|フレンドリ名|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a>オーバーロード演算子 ==
 オーバーロードは`operator ==`非常に複雑です。 演算子のセマンティクスは、 などの<xref:System.Object.Equals%2A?displayProperty=nameWithType>他のメンバーと互換性がある必要があります。

### <a name="conversion-operators"></a>変換演算子
 変換演算子は、ある型から別の型への変換を可能にする単項演算子です。 演算子は、オペランドまたは戻り値の型で静的メンバーとして定義する必要があります。 変換演算子には、暗黙的および明示的の 2 種類があります。

 ❌このような変換がエンド ユーザーによって明確に予期されない場合は、変換演算子を提供しないでください。

 ❌型のドメインの外部で変換演算子を定義しないでください。

 たとえば、 <xref:System.Int32>、、<xref:System.Double>および<xref:System.Decimal>は、すべて数値型<xref:System.DateTime>ですが、数値型は、そうではありません。 したがって、 に`Double(long)`変換する変換演算子は必要`DateTime`ありません。 このような場合はコンストラクタが好ましい。

 ❌変換が損失を生じやすい場合は、暗黙の変換演算子を提供しないでください。

 For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`. 変換が損失を生じかなくても、明示的な変換演算子を指定できます。

 ❌暗黙的なキャストから例外をスローしないでください。

 エンド ユーザーは、変換が行われていることに気づいていない可能性があるため、何が起こっているのかを理解することは非常に困難です。

 キャスト演算子を<xref:System.InvalidCastException?displayProperty=nameWithType>呼び出すと損失変換が発生し、演算子のコントラクトが損失変換を許可しない場合は、✔️ DO スローします。

 *2005年、2009年©マイクロソフト株式会社。すべての権利が予約されています。*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
