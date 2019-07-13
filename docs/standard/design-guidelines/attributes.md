---
title: 属性
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: KrzysztofCwalina
ms.openlocfilehash: 6d4cc6615b7f7346e9c8fc2a7264025f318c8a3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785568"
---
# <a name="attributes"></a>属性
<xref:System.Attribute?displayProperty=nameWithType> カスタム属性を定義するために使用する基本クラス。  
  
 属性は、アセンブリ、型、メンバー、およびパラメーターなどのプログラミング要素に追加できる注釈です。 アセンブリのメタデータに格納されていて、リフレクション Api を使用して実行時にアクセスできます。 たとえば、フレームワークを定義、 <xref:System.ObsoleteAttribute>、型またはメンバーは推奨されていることを示す、型またはメンバーに適用できます。  
  
 属性には、1 つ以上のプロパティ、属性に関連する追加のデータを受け渡すことができます。 たとえば、`ObsoleteAttribute`のリリースに関する追加情報を実行することが、型またはメンバーが非推奨とし、廃止された API を置き換える新しい Api の説明。  
  
 属性が適用されるときに、属性の一部のプロパティを指定する必要があります。 これらと呼びます必要なプロパティまたは必須の引数を位置指定コンス トラクターのパラメーターとして表されるためです。 たとえば、<xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A>のプロパティ、<xref:System.Diagnostics.ConditionalAttribute>は必要なプロパティです。  
  
 属性を適用した場合に指定する必ずしもプロパティは省略可能なプロパティ (または省略可能な引数) と呼ばれます。 設定可能なプロパティで表されます。 コンパイラは、属性が適用されるときに、これらのプロパティを設定する特別な構文を提供します。 たとえば、<xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>プロパティは省略可能な引数を表します。  
  
 **✓ DO** 「属性」サフィックスを持つカスタム属性クラスの名前  
  
 **✓ DO** 適用、<xref:System.AttributeUsageAttribute>カスタム属性にします。  
  
 **✓ DO** 省略可能な引数の設定可能なプロパティを提供します。  
  
 **✓ DO** 必須の引数の取得専用のプロパティを提供します。  
  
 **✓ DO** 必須の引数に対応するプロパティを初期化するコンス トラクターのパラメーターを指定します。 各パラメーターは、対応するプロパティとして (大文字小文字が異なる) には、同じ名前が必要です。  
  
 **X AVOID** 省略可能な引数に対応するプロパティを初期化するコンス トラクターのパラメーターを指定します。  
  
 つまり、コンス トラクターと setter の両方で設定できるプロパティがありません。 このガイドラインでは非常に明示的などの引数は省略可能ですし、これは必須であり、2 つの方法で同じことを行う必要はなくなります。  
  
 **X AVOID** カスタム属性のコンス トラクターのオーバー ロードします。  
  
 コンス トラクターの 1 つだけのことを明確に伝達をユーザーにどの引数が必要ですし、これは省略可能です。  
  
 **✓ DO** 可能であれば、カスタム属性クラスをシールします。 これにより、属性の参照、高速化。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
