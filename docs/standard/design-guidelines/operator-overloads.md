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
author: KrzysztofCwalina
ms.openlocfilehash: 441dc2777cd8d221300c526b6b31a647af60ca71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756859"
---
# <a name="operator-overloads"></a>演算子のオーバーロード
演算子のオーバー ロードは、組み込みの言語プリミティブとして表示するフレームワークの種類を許可します。  
  
 許可されている、いくつかの状況で便利ですが、演算子のオーバー ロードを慎重に使用してください。 演算子のオーバー ロードがされて悪用などの単純なメソッドにする必要がある操作の演算子を使用するフレームワークの設計者を開始するときに多くの場合があります。 次のガイドラインを使用するとが演算子のオーバー ロードを使用するタイミングと方法を決定できます。  
  
 **X AVOID** を除く演算子のオーバー ロードを定義する必要があります (組み込み) のプリミティブ型と感じての種類でします。  
  
 **✓ CONSIDER** 演算子のオーバー ロードを定義する型がプリミティブ型のように感じる必要があります。  
  
 たとえば、<xref:System.String?displayProperty=nameWithType>が`operator==`と`operator!=`定義します。  
  
 **✓ DO** 番号を表す構造体で演算子オーバー ロードを定義する (など<xref:System.Decimal?displayProperty=nameWithType>)。  
  
 **X DO NOT** 演算子のオーバー ロードを定義するときに分別して使用します。  
  
 演算子のオーバー ロードは、それがすぐに明らかななります操作の結果に便利です。 たとえば、理にかなって 1 を減算できます<xref:System.DateTime>別の`DateTime`を取得し、<xref:System.TimeSpan>します。 ただし、適切なは、共用体の 2 つのデータベース クエリに論理演算子を使用するかをシフト演算子を使用して、ストリームへの書き込みはできません。  
  
 **X DO NOT** オーバー ロードを定義する型のオペランドの少なくとも 1 つがない限り、演算子がオーバー ロードを提供します。  
  
 **✓ DO** 対称的に演算子をオーバー ロードします。  
  
 たとえば、オーバー ロードする場合、 `operator==`、オーバー ロードもする必要があります、`operator!=`します。 同様に、オーバー ロードする場合、 `operator<`、オーバー ロードする必要がありますも、`operator>`など。  
  
 **✓ CONSIDER** 各オーバー ロードされた演算子に対応するフレンドリ名を持つメソッドを提供します。  
  
 多くの言語は、演算子のオーバー ロードをサポートしていません。 このため、演算子をオーバー ロードする型が同等の機能を提供します。 ドメイン固有の適切な名前を持つセカンダリ メソッドを含めることをお勧めします。  
  
 次の表には、演算子と、対応するメソッドのフレンドリ名の一覧が含まれています。  
  
|C# 演算子記号|メタデータ名|表示名|  
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
  
### <a name="overloading-operator-"></a>演算子をオーバー ロード = =  
 オーバー ロード`operator ==`は非常に複雑になります。 演算子のセマンティクスをなど、他のいくつかのメンバーと互換性がある必要があります<xref:System.Object.Equals%2A?displayProperty=nameWithType>します。  
  
### <a name="conversion-operators"></a>変換演算子  
 変換演算子は、単項演算子を別の型に変換できるようにします。 演算子は、オペランドまたは戻り値の型のいずれかの静的メンバーとして定義する必要があります。 変換演算子の 2 種類があります。 明示的および暗黙的な。  
  
 **X DO NOT** エンドユーザーでこのような変換が明確に予期されていない場合は、変換演算子を提供します。  
  
 **X DO NOT** 型のドメインの外部の変換演算子を定義します。  
  
 たとえば、 <xref:System.Int32>、 <xref:System.Double>、および<xref:System.Decimal>はのすべての数値型に対し<xref:System.DateTime>はありません。 そのため、ことはありません変換への変換演算子を`Double(long)`を`DateTime`します。 このような場合、コンス トラクターが優先されます。  
  
 **X DO NOT** 変換が損失を伴う可能性がある場合は、暗黙的な変換演算子を提供します。  
  
 たとえば、存在することはできませんからの暗黙的な変換`Double`に`Int32`ため`Double`よりも広い範囲が`Int32`します。 変換ではデータ損失の可能性がある場合でも、明示的な変換演算子を指定できます。  
  
 **X DO NOT** 暗黙的なキャストから例外をスローします。  
  
 エンドユーザーへの変換が行われていることが認識されない可能性があります、ために何が起こっているかを理解するは困難です。  
  
 **✓ DO** スロー<xref:System.InvalidCastException?displayProperty=nameWithType>でキャスト演算子への呼び出しが損失を伴う変換と演算子のコントラクトでは、非可逆の変換は許可されません。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
