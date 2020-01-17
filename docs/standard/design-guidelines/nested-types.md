---
title: Nested Types
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: 3467851aa767efcd0557e8a412cd36316a48b9b0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709154"
---
# <a name="nested-types"></a>Nested Types
入れ子になった型は、外側の型と呼ばれる別の型のスコープ内で定義された型です。 入れ子になった型は、それを囲む型のすべてのメンバーにアクセスできます。 たとえば、外側の型で定義されているプライベートフィールドと、それを囲む型のすべての先祖で定義されている保護されたフィールドにアクセスできます。  
  
 一般に、入れ子になった型は控えめに使用する必要があります。 直接呼び出すべきではないいくつかの理由があります。 一部の開発者は、この概念について完全には理解していません。 たとえば、これらの開発者は、入れ子になった型の変数を宣言する構文で問題が発生する可能性があります。 入れ子になった型もその外側の型と密接に結び付いています。そのため、汎用型には適していません。  
  
 入れ子になった型は、それを囲む型の実装の詳細をモデリングする場合に最適です。 エンドユーザーは、入れ子にされた型の変数を宣言する必要はほとんどなく、入れ子になった型を明示的にインスタンス化する必要はほとんどありません。 たとえば、コレクションの列挙子は、そのコレクションの入れ子にされた型にすることができます。 列挙子は、通常、それを囲む型によってインスタンス化されます。また、多くの言語では foreach ステートメントがサポートされるため、列挙子の変数はエンドユーザーが宣言することはほとんどありません。  
  
 **✓ DO** 入れ子にされた型とその外側の型間の関係のあるメンバーのアクセシビリティのセマンティクスは次のことをお勧めときに、入れ子にされた型を使用します。  
  
 **X DO NOT** 論理的なグループとしてパブリック入れ子にされた型を使用して構築以外の場合はこの名前空間を使用します。  
  
 **X AVOID** 入れ子にされた型をパブリックに公開します。 唯一の例外は、入れ子にされた型の変数は、サブクラス化やその他の高度なカスタマイズシナリオなど、まれなシナリオでのみ宣言する必要がある場合に限られます。  
  
 **X DO NOT** 型が、含んでいる型の外部で参照されている可能性が高い場合は、入れ子にされた型を使用します。  
  
 たとえば、クラスで定義されたメソッドに渡される列挙型は、クラスで入れ子にされた型として定義することはできません。  
  
 **X DO NOT** クライアント コードでインスタンス化する必要がある場合は、入れ子にされた型を使用します。  型にパブリックコンストラクターがある場合は、入れ子になっていない可能性があります。  
  
 型がインスタンス化できる場合、型がそれ自体のフレームワーク内に配置されていることを示しているように見えます (作成、操作、外部型を使用せずに破棄できます)。したがって、入れ子にすることはできません。 外部型に関係なく、外側の型の外部で内部型を広く再利用することはできません。  
  
 **X DO NOT** インターフェイスのメンバーとして入れ子にされた型を定義します。 多くの言語では、このようなコンストラクトはサポートされていません。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
