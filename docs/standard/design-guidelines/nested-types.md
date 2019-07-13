---
title: 入れ子にされた型
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
author: KrzysztofCwalina
ms.openlocfilehash: 22c14d05105154ff642cb8a44eda8e7c5d0575e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756872"
---
# <a name="nested-types"></a>入れ子にされた型
入れ子になった型は、それを囲む型と呼ばれる別の型のスコープ内で定義されている型です。 入れ子にされた型が、その外側の型のすべてのメンバーにアクセスします。 たとえば、それを囲む型のすべての先祖で定義されているフィールドを保護して、外側の型で定義されてプライベート フィールドにアクセス権があります。  
  
 一般に、控えめ入れ子にされた型に使用する必要があります。 直接呼び出すべきではないいくつかの理由があります。 一部の開発者の概念を熟知していません。 これらの開発者では、入れ子にされた型の変数の宣言の構文に問題があるなどがあります。 入れ子にされた型は、その外側の型でも非常に緊密に結合されていて、そのため、汎用型であることには適していません。  
  
 入れ子にされた型は、それを囲む型の実装の詳細をモデル化するために最適です。 エンドユーザーは、入れ子にされた型の変数を宣言する必要はほとんどとほとんどない、入れ子にされた型を明示的にインスタンス化する必要があります。 たとえば、コレクションの列挙子は、そのコレクションの入れ子にされた型にできます。 列挙子がその外側の型でインスタンス化は、通常、列挙子変数に、エンドユーザーが宣言することはほとんどありませんがあるため、多くの言語では、foreach ステートメントをサポート、.  
  
 **✓ DO** 入れ子にされた型とその外側の型間の関係のあるメンバーのアクセシビリティのセマンティクスは次のことをお勧めときに、入れ子にされた型を使用します。  
  
 **X DO NOT** 論理的なグループとしてパブリック入れ子にされた型を使用して構築以外の場合はこの名前空間を使用します。  
  
 **X AVOID** 入れ子にされた型をパブリックに公開します。 唯一の例外は、入れ子にされた型の変数をサブクラスまたはその他の高度なカスタマイズ シナリオなどのまれなシナリオでのみ宣言する必要があるかどうかです。  
  
 **X DO NOT** 型が、含んでいる型の外部で参照されている可能性が高い場合は、入れ子にされた型を使用します。  
  
 たとえば、クラスで定義されたメソッドに渡される列挙型はクラスの入れ子にされた型として定義されませんする必要があります。  
  
 **X DO NOT** クライアント コードでインスタンス化する必要がある場合は、入れ子にされた型を使用します。  型のパブリック コンス トラクターの場合する必要がありますネストいない可能性があります。  
  
 型が、独自のフレームワーク内の場所を示すために思えます型をインスタンス化する場合 (できます作成し、それに伴う作業し、これまで、外部型を使用せず、それを破棄)、そのため、ネストいない必要があります。 内部型する必要がありますいない広範囲に再利用、リレーションシップがない場合は、外側の型の外部で外側の型にもします。  
  
 **X DO NOT** インターフェイスのメンバーとして入れ子にされた型を定義します。 多くの言語は、そのようなコンストラクトをサポートしていません。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
