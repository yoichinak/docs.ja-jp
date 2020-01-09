---
title: 抽象クラスのデザイン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 19482199648a8fb9c4b2c796fb1ab5d62c896abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709596"
---
# <a name="abstract-class-design"></a>抽象クラスのデザイン
**X** 抽象型に public または protected のコンストラクターを定義しないでください。  
  
 コンストラクターは、ユーザーがその型のインスタンスを作成する必要がないならば public であるべきではありません。 抽象型のインスタンスを作成することはできないので、public なコンストラクターを持つ抽象型は設計が間違っており、ユーザーに誤解を招きます。  
  
 **✓** 抽象クラスには、protected または internal のコンストラクターを定義してください。  
  
 protected コンストラクターはより一般的で、派生型が作成された時に基底クラスが独自の初期化を実行できるようにします。  
  
 internal コンストラクターは、その具象実装をアセンブリ内部に制限するために用いることができます。  
  
 **✓** 出荷する抽象クラスから継承する具象型を少なくとも 1 つ提供してください。  
  
 こうすることにより、抽象クラスのデザインを検証できます。 たとえば、<xref:System.IO.FileStream?displayProperty=nameWithType>は<xref:System.IO.Stream?displayProperty=nameWithType>の具象実装です。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
