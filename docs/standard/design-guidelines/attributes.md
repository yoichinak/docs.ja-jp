---
title: 属性
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: ff38cfdc228fd1eae1ace734ed2688c62c66499a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709557"
---
# <a name="attributes"></a>属性
<xref:System.Attribute?displayProperty=nameWithType> は、カスタム属性を定義するために使用される基本クラスです。  
  
 属性は、アセンブリ、型、メンバー、パラメーターなどのプログラミング要素に追加できる注釈です。 これらは、アセンブリのメタデータに格納され、リフレクション Api を使用して実行時にアクセスできます。 たとえば、フレームワークは <xref:System.ObsoleteAttribute>を定義します。これを型またはメンバーに適用して、型またはメンバーが非推奨とされたことを示すことができます。  
  
 属性には、属性に関連する追加データを格納する1つ以上のプロパティを含めることができます。 たとえば、`ObsoleteAttribute` は、型またはメンバーが非推奨とされたリリースに関する追加情報を伝達し、新しい Api の説明で古い API を置き換えることができます。  
  
 属性を適用するときは、属性の一部のプロパティを指定する必要があります。 これらは、位置指定コンストラクターパラメーターとして表現されるため、必須プロパティまたは必須の引数と呼ばれます。 たとえば、<xref:System.Diagnostics.ConditionalAttribute> の <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> プロパティは必須プロパティです。  
  
 属性が適用されるときに必ずしも指定する必要がないプロパティは、省略可能なプロパティ (または省略可能な引数) と呼ばれます。 これらは、設定可能なプロパティによって表されます。 コンパイラは、属性が適用されるときにこれらのプロパティを設定するための特別な構文を提供します。 たとえば、<xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> プロパティは省略可能な引数を表します。  
  
 **✓ DO** 「属性」サフィックスを持つカスタム属性クラスの名前  
  
 **✓ DO** 適用、<xref:System.AttributeUsageAttribute>カスタム属性にします。  
  
 **✓ DO** 省略可能な引数の設定可能なプロパティを提供します。  
  
 **✓ DO** 必須の引数の取得専用のプロパティを提供します。  
  
 **✓ DO** 必須の引数に対応するプロパティを初期化するコンス トラクターのパラメーターを指定します。 各パラメーターには、対応するプロパティと同じ名前 (大文字と小文字が異なる) を指定する必要があります。  
  
 **X AVOID** 省略可能な引数に対応するプロパティを初期化するコンス トラクターのパラメーターを指定します。  
  
 つまり、コンストラクターとセッターの両方で設定できるプロパティはありません。 このガイドラインでは、省略可能な引数と必須の引数を明確に指定します。これにより、2つの方法で同じことを行うことが回避されます。  
  
 **X AVOID** カスタム属性のコンス トラクターのオーバー ロードします。  
  
 コンストラクターが1つだけの場合は、どの引数が必須であり、省略可能であるかをユーザーに明確に伝えます。  
  
 **✓ DO** 可能であれば、カスタム属性クラスをシールします。 これにより、属性の参照が高速になります。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
