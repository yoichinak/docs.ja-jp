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
ms.openlocfilehash: 3e2fe7168bd0029d8f0e8f69a136c9089032973f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709024"
---
# <a name="type-design-guidelines"></a>型のデザインのガイドライン
CLR の観点からは、参照型と値型のカテゴリは2つだけですが、フレームワークの設計について説明するために、型をより多くの論理グループに分割し、それぞれに固有のデザインルールを使用します。  
  
 クラスは、参照型の一般的なケースです。 多くのフレームワークでは、多くの型が構成されています。 クラスは、サポートされているオブジェクト指向の機能の豊富なセットと、その一般的な適用性を持ちます。 基本クラスと抽象クラスは、機能拡張に関連する特殊な論理グループです。  
  
 インターフェイスは、参照型と値型の両方で実装できる型です。 これにより、参照型と値型のポリモーフィック階層のルートとして機能することができます。 さらに、インターフェイスを使用して、CLR でネイティブにサポートされていない複数の継承をシミュレートすることもできます。  
  
 構造体は値型の一般的なケースであり、言語プリミティブと同様に、小規模な単純型用に予約する必要があります。  
  
 列挙型は、曜日やコンソールの色など、短い値のセットを定義するために使用される特殊な値型です。  
  
 静的クラスは、静的メンバーのコンテナーとして使用される型です。 一般的に、他の操作へのショートカットを提供するために使用されます。  
  
 デリゲート、例外、属性、配列、およびコレクションは、特定の用途を想定した参照型のすべての特殊なケースであり、その設計と使用に関するガイドラインについては、このブックの別の部分で説明します。  
  
 **✓ DO** 各型が適切に定義された一連の関連するメンバーは、関連付けられていない機能のランダムなコレクションだけでなくであることを確認します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [クラスまたは構造体の選択](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [抽象クラスのデザイン](../../../docs/standard/design-guidelines/abstract-class.md)  
 [静的クラスのデザイン](../../../docs/standard/design-guidelines/static-class.md)  
 [インターフェイスのデザイン](../../../docs/standard/design-guidelines/interface.md)  
 [構造体のデザイン](../../../docs/standard/design-guidelines/struct.md)  
 [列挙型デザイン](../../../docs/standard/design-guidelines/enum.md)  
 [入れ子にされた型](../../../docs/standard/design-guidelines/nested-types.md)  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
