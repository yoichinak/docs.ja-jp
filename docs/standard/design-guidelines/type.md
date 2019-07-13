---
title: 型のデザインのガイドライン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: KrzysztofCwalina
ms.openlocfilehash: 16f2a095f461a406eedbd2b34b0c91d3ac43bbe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650103"
---
# <a name="type-design-guidelines"></a>型のデザインのガイドライン
CLR の観点からは、型の 2 つのカテゴリがあります: 参照型と値の型: フレームワークの設計に関する詳細については、するために、それぞれに独自の特定のデザイン規則より論理的にグループの種類を分割しますが、します。  
  
 クラスは、参照型の一般的なケースです。 ほとんどのフレームワークの型の大部分を構成します。 クラスは、豊富なオブジェクト指向の機能がサポートされるを設定して、一般的な適用性を人気を助かりました。 基底クラスと抽象クラスは、拡張機能に関連する、特殊な論理グループです。  
  
 インターフェイスは、参照型と値の型の両方で実装できる型です。 したがって、参照型と値の型のポリモーフィックな階層のルートとして使用ができます。 さらに、インターフェイスは、CLR によってネイティブでサポートされていない複数の継承をシミュレートするために使用できます。  
  
 構造体の値型の一般的なケースは、小規模で単純な種類、言語プリミティブのように予約されている必要があります。  
  
 列挙型は、週、コンソールの色の日などの値の短いセットを定義するのに使用される値型の特殊なケースです。  
  
 静的クラスは、型の静的メンバーのコンテナーを意図したものです。 その他の操作へのショートカットを提供するよく使用されます。  
  
 デリゲート、例外、属性、配列、およびコレクションは、特定の用途のためのもので、参照型のすべての特殊なケースと、この書籍での設計と使用法のガイドラインは別の場所について説明します。  
  
 **✓ DO** 各型が適切に定義された一連の関連するメンバーは、関連付けられていない機能のランダムなコレクションだけでなくであることを確認します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [クラスまたは構造体の選択](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [抽象クラスのデザイン](../../../docs/standard/design-guidelines/abstract-class.md)  
 [静的クラスのデザイン](../../../docs/standard/design-guidelines/static-class.md)  
 [インターフェイスのデザイン](../../../docs/standard/design-guidelines/interface.md)  
 [構造体のデザイン](../../../docs/standard/design-guidelines/struct.md)  
 [列挙型デザイン](../../../docs/standard/design-guidelines/enum.md)  
 [入れ子にされた型](../../../docs/standard/design-guidelines/nested-types.md)  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
