---
title: メンバーのデザインのガイドライン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
author: KrzysztofCwalina
ms.openlocfilehash: d7023bbe59eb3590af47952a2fe24c5f40b3ca68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945523"
---
# <a name="member-design-guidelines"></a>メンバーのデザインのガイドライン
メソッド、プロパティ、イベント、コンス トラクター、およびフィールドは、メンバーとしてまとめて呼ばれます。 メンバーが、最終的に、フレームワークのエンドユーザーに、フレームワークの機能が公開されていることを意味します。  
  
 メンバーは、仮想または非仮想、具象か抽象クラスで静的メソッドまたはインスタンスにできるし、ユーザー補助機能のいくつかの異なるスコープを持つことができます。 さまざまな種類すべてでは、驚異的な表現力を提供しますが、同時に、framework デザイナー側注意が必要です。  
  
 この章では、任意の型のメンバーを設計するときに従う必要がありますの基本的なガイドラインを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [メンバーのオーバーロード](../../../docs/standard/design-guidelines/member-overloading.md)  
 [プロパティのデザイン](../../../docs/standard/design-guidelines/property.md)  
 [コンストラクターのデザイン](../../../docs/standard/design-guidelines/constructor.md)  
 [イベントのデザイン](../../../docs/standard/design-guidelines/event.md)  
 [フィールドのデザイン](../../../docs/standard/design-guidelines/field.md)  
 [拡張メソッド](../../../docs/standard/design-guidelines/extension-methods.md)  
 [演算子のオーバーロード](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [パラメーターのデザイン](../../../docs/standard/design-guidelines/parameter-design.md)  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
