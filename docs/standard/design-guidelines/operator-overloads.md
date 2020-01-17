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
ms.openlocfilehash: 4cea3c17de40a873d977223f36b6dcef4f2c2d78
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709141"
---
# <a name="operator-overloads"></a>演算子のオーバーロード
演算子のオーバーロードでは、フレームワーク型を組み込みの言語プリミティブとして表示できます。  
  
 一部の状況では許可および便利ですが、演算子のオーバーロードは慎重に使用する必要があります。 多くの場合、演算子のオーバーロードは不正使用されています。たとえば、framework デザイナーが、単純なメソッドである必要がある操作に対して演算子の使用を開始した場合などです。 次のガイドラインは、演算子のオーバーロードを使用するタイミングと方法を決定するのに役立ちます。  
  
 **X AVOID** を除く演算子のオーバー ロードを定義する必要があります (組み込み) のプリミティブ型と感じての種類でします。  
  
 **✓ CONSIDER** 演算子のオーバー ロードを定義する型がプリミティブ型のように感じる必要があります。  
  
 たとえば、<xref:System.String?displayProperty=nameWithType> に `operator==` と `operator!=` が定義されているとします。  
  
 **✓ DO** 番号を表す構造体で演算子オーバー ロードを定義する (など<xref:System.Decimal?displayProperty=nameWithType>)。  
  
 **X DO NOT** 演算子のオーバー ロードを定義するときに分別して使用します。  
  
 演算子のオーバーロードは、操作の結果がすぐにわかる場合に便利です。 たとえば、ある <xref:System.DateTime> を別の `DateTime` から減算し、<xref:System.TimeSpan>を取得できるようにするのは理にかなっています。 ただし、2つのデータベースクエリを結合する場合や、shift 演算子を使用してストリームに書き込む場合は、論理和演算子を使用するのは適切ではありません。  
  
 **X DO NOT** オーバー ロードを定義する型のオペランドの少なくとも 1 つがない限り、演算子がオーバー ロードを提供します。  
  
 **✓ DO** 対称的に演算子をオーバー ロードします。  
  
 たとえば、`operator==`をオーバーロードする場合は、`operator!=`もオーバーロードする必要があります。 同様に、`operator<`をオーバーロードする場合は、`operator>`もオーバーロードする必要があります。  
  
 **✓ CONSIDER** 各オーバー ロードされた演算子に対応するフレンドリ名を持つメソッドを提供します。  
  
 多くの言語では、演算子のオーバーロードはサポートされていません。 このため、オーバーロード演算子には、同等の機能を提供するドメイン固有の適切な名前を持つ二次的なメソッドが含まれていることをお勧めします。  
  
 次の表に、演算子とそれに対応するわかりやすいメソッド名の一覧を示します。  
  
|C#演算子シンボル|メタデータ名|[フレンドリ名]|  
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
  
### <a name="overloading-operator-"></a>オーバーロード演算子 = =  
 `operator ==` のオーバーロードは非常に複雑です。 演算子のセマンティクスは、<xref:System.Object.Equals%2A?displayProperty=nameWithType>など、他のいくつかのメンバーと互換性がある必要があります。  
  
### <a name="conversion-operators"></a>変換演算子  
 変換演算子は、ある型から別の型への変換を可能にする単項演算子です。 演算子は、オペランドまたは戻り値の型のいずれかの静的メンバーとして定義する必要があります。 変換演算子には、暗黙的と明示的の2種類があります。  
  
 **X DO NOT** エンドユーザーでこのような変換が明確に予期されていない場合は、変換演算子を提供します。  
  
 **X DO NOT** 型のドメインの外部の変換演算子を定義します。  
  
 たとえば、<xref:System.Int32>、<xref:System.Double>、および <xref:System.Decimal> はすべて数値型ですが、<xref:System.DateTime> はありません。 したがって、`Double(long)` を `DateTime`に変換する変換演算子は存在しない必要があります。 このような場合は、コンストラクターを使用することをお勧めします。  
  
 **X DO NOT** 変換が損失を伴う可能性がある場合は、暗黙的な変換演算子を提供します。  
  
 たとえば、`Double` の範囲が `Int32`よりも広いため、`Double` から `Int32` への暗黙的な変換を行うことはできません。 変換が損失する可能性がある場合でも、明示的な変換演算子を指定できます。  
  
 **X DO NOT** 暗黙的なキャストから例外をスローします。  
  
 変換が行われていることを認識していない可能性があるため、エンドユーザーは何が起こっているかを理解することは非常に困難です。  
  
 **✓ DO** スロー<xref:System.InvalidCastException?displayProperty=nameWithType>でキャスト演算子への呼び出しが損失を伴う変換と演算子のコントラクトでは、非可逆の変換は許可されません。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
