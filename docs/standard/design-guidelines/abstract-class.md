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
author: KrzysztofCwalina
ms.openlocfilehash: 6eec3bb4575b89c6476e6c3410050c705141777f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550413"
---
# <a name="abstract-class-design"></a>抽象クラスのデザイン
**X** 抽象型に public または protected のコンストラクターを**定義しないでください。**

コンストラクターは、ユーザーがその型のインスタンスを作成する必要がないならば public であるべきではありません。抽象型のインスタンスを作成することはできないので、public なコンストラクターを持つ抽象型は設計が間違っており、ユーザーに誤解を招きます。

**✓** 抽象クラスには、protected または internal のコンストラクターを**定義してください。**

protected コンストラクターはより一般的で、派生型が作成された時に基底クラスが独自の初期化を実行できるようにします。

internal コンストラクターは、その具象実装をアセンブリ内部に制限するために用いることができます。

**✓** 出荷する抽象クラスから継承する具象型を少なくとも 1 つ**提供してください。**

こうすることにより、抽象クラスのデザインを検証できます。たとえば、<xref:System.IO.FileStream?displayProperty=nameWithType>は<xref:System.IO.Stream?displayProperty=nameWithType>の具象実装です。

*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

*Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*

## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
