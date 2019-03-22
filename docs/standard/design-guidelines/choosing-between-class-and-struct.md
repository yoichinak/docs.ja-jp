---
title: クラスまたは構造体の選択
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
author: KrzysztofCwalina
ms.openlocfilehash: a47e43b2387362500d46c8e531f16d004d823c4c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565866"
---
# <a name="choosing-between-class-and-struct"></a>クラスまたは構造体の選択
すべての framework デザイナーに直面して基本的な設計上の決定の 1 つが、クラス (参照型)、または構造体 (値型) として型を設計するかどうか。 参照型と値の型の動作の違いの理解は、この選択を行うに不可欠です。

 最初の差。 参照型と値の型は、参照型とガベージ コレクションのヒープに割り当てられた値の型が割り当てられたスタックのいずれかまたはインラインで含まれている型し割り当て解除されたときに検討のスタックアンワインドまたは取得、含んでいる型の割り当てを解除する場合。 したがって、値型の割り当てと解放は、一般的な参照型の割り当てと解放よりも低コストになります。

 次に、参照型の配列では、行外、つまり配列要素に、ヒープ上にある参照型のインスタンスへの参照のみが割り当てられます。 値型の配列には、インライン、つまり、配列要素は、値の型の実際のインスタンスが割り当てられます。 したがって、値型の配列の割り当てと解放は、参照型の配列の割り当てと解放よりもかなり安くなります。 さらに、ほとんどの場合は、値型の配列と、参照の局所性量が高くが発生します。

 次の相違点は、メモリ使用量に関連します。 値型は、参照型またはいずれかを実装するインターフェイスにキャストするときをボックス化を取得します。 ボックス化解除された取得値の型にキャストするとき。 ボックス オブジェクトはヒープに割り当てられ、ガベージ コレクションが、あまりボックス化とボックス化解除するため、ヒープ、ガベージ コレクター、および最終的には、アプリケーションのパフォーマンスに悪影響を及ぼすことができます。  これに対し、このようなボックス化は行われません、参照型にキャストされます。 (詳細については、次を参照してください。[ボックス化とボックス化解除](../../csharp/programming-guide/types/boxing-and-unboxing.md))。

 次に、参照型の割り当ては、値型の割り当て値全体をコピーする一方、参照をコピーします。 そのため、大規模な参照型の割り当ては、大きな値の型の割り当てよりも低コストです。

 最後に、値の型が値によって渡されますが、参照型は、参照によって渡されます。 参照型のインスタンスへの変更では、インスタンスを指すすべての参照に影響します。 値型のインスタンスは、値によって渡されるときにコピーされます。 値型のインスタンスが変更されたときに、もちろんには影響しません、そのコピーのいずれか。 コピーは、ユーザーが明示的に作成されませんが、引数が渡される、または返される値を返すときに暗黙的に作成される、ために、変更可能な値の型は、多数のユーザーに混乱があります。 そのため、値の型は変更できません。

 一般に、フレームワーク内の型の大部分は、クラスできなければなりません。 ただし、状況によっては、値型の特性ようにより適切に構造体を使用するがあります。

 **✓ CONSIDER** 型のインスタンスは小さく、一般的な有効期間が短いまたはその他のオブジェクトに埋め込まれている一般的な場合は、クラスの代わりに構造体を定義することです。

 **X AVOID** すべて次の特徴の種類があるない限り、構造体を定義します。

-   プリミティブ型のような 1 つの値を論理的に表す (`int`、`double`など。)。

-   16 バイト未満のサイズのインスタンスがあります。

-   変更可能なことはできません。

-   頻繁にボックス化することはありません。

 他のすべてのケースでは、クラスとして、型を定義する必要があります。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*

## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
