---
title: 抽象化の実装用の基本クラス
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
author: KrzysztofCwalina
ms.openlocfilehash: 6811423258481fcbae24743c9b17f3f20c379c58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785542"
---
# <a name="base-classes-for-implementing-abstractions"></a>抽象化の実装用の基本クラス
厳密に言えば、別のクラスがそこから派生する場合、クラスは、基底クラスになります。 ここでは、ただし、基本クラスは、共通の抽象化を提供または一部を再利用するには、他のクラスの既定の実装が継承する主な目的としたクラス。 通常、基底クラスは、階層のルートにある抽象化と下部にあるいくつかのカスタム実装の間の継承階層の途中で配置されています。  
  
 これらは、抽象化を実装するための実装のヘルパーとして機能します。 たとえば、項目の順序付けられたコレクションのフレームワークの抽象化の 1 つは、<xref:System.Collections.Generic.IList%601>インターフェイス。 実装する<xref:System.Collections.Generic.IList%601>、簡単ではありませんし、そのため、いくつかの基本クラスは、フレームワークなど<xref:System.Collections.ObjectModel.Collection%601>と<xref:System.Collections.ObjectModel.KeyedCollection%602>、カスタム コレクションを実装するためのヘルパーとして機能します。  
  
 基底クラスは、通常は、単独で抽象化として機能するのに適したが多すぎるの実装を格納する傾向があるためです。 たとえば、`Collection<T>`基底クラスには、大量非ジェネリックが実装しているという事実に関連する実装にはが含まれています`IList`(非ジェネリック コレクションでより適切に統合) へのインターフェイスとは、という事実に格納された項目のコレクション。そのフィールドのいずれかでメモリ。  
  
 既に説明したようの基本クラスは抽象化を実装する必要があるユーザーにご協力を提供することができますが、同時に重大な責任になることができます。 継承階層の深さを増やすし、したがって概念的には、フレームワークが複雑になる、サーフェス領域を追加します。 そのため、フレームワークのユーザーに大きな価値を提供する場合にのみ、基本クラスを使用する必要があります。 これらを基本クラスから継承ではなく内部の実装への委任で大文字と小文字をことを検討するフレームワークの実装時にのみ値を提供する場合に避ける必要があります。  
  
 **✓ CONSIDER** 抽象メンバーが含まれている場合でも、基本クラスの抽象です。 これをユーザーに明確に伝達する、クラスが継承するためだけに設計されています。  
  
 **✓ CONSIDER** 主要なシナリオの種類から別の名前空間の基本クラスを配置することです。 定義上、基底クラスは高度な機能拡張シナリオのためのものし、そのため、多くのユーザーにとって重要ではありません。  
  
 **X AVOID** クラスは、パブリック Api で使用する場合は、"Base"サフィックスを持つ基本クラスを名前付けします。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
