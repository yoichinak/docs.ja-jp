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
すべてのフレームワーク設計者が直面する基本的な設計上の決定の 1 つが、ある型をクラス (参照型) として設計するか、構造体 (値型) として設計するかという点です。この決定を下すためには、参照型と値の型の動作の違いをよく理解しておく必要があります。

取り上げる最初の違いは、メモリー割り当てと解放に関するものです。参照型はヒープ メモリに割り当てられガベージ コレクションの対象となります。一方、値型はスタック メモリか、それを含む型の内部に割り当てられ、スタックがアンワインドされるかそれを含む型が解放される時に解放されます。それで一般的に、値型の割り当てと解放は、参照型よりも低コストです。

次の違いは配列に関するものです。参照型の配列では、インスタンスは配列外に割り当てられます。つまり、配列要素はヒープ上にあるインスタンスへの参照であるということです。値型の配列はインラインです。つまり、配列要素は値型の実際のインスタンスであるということです。したがって、値型の配列の割り当てと解放は、参照型の配列と比べてかなり低コストになります。さらに、ほとんどのケースでは、値型の配列では参照の局所性がとても良くなります。

次の相違点は、メモリ使用量に関するものです。値型は、参照型やそれが実装するインターフェイスにキャストされる時にボックス化されます。そして、値型に再キャストされたときにボックス化解除されます。ボックス化されたオブジェクトはヒープに割り当てられ、ガベージ コレクションの対象となるため、ボックス化とボックス化解除があまりに頻繁に行われると、ヒープ メモリ、ガベージ コレクター、そして最終的にはアプリケーション全体のパフォーマンスに悪影響を及ぼす可能性があります。これに対し、参照型はキャストされるため、このようなボックス化は行われません。 (詳細については、[ボックス化とボックス化解除](../../csharp/programming-guide/types/boxing-and-unboxing.md)を参照してください。)

次の点は、コピーに関するものです。参照型が参照のみをコピーする一方、値型は値全体をコピーします。そのため、大きな参照型の割り当ては、大きな値型の割り当てよりも低コストです。

最後の点です。値型は値渡しされますが、参照型は参照渡しされます。参照型インスタンスへの変更は、そのインスタンスを指すすべての参照に影響します。値型インスタンスは、値渡しされるときにコピーされます。それで、値型インスタンスが変更されたても、その他のコピーにはもちろんには影響しません。。ユーザーが明示的にそうしなくても、引数を渡したり戻り値を返したりするときに暗黙的にコピーが作成されます。それで、変更可能な値型は、多くのユーザーにとって混乱の元です。そのため、値型は変更不可能であるべきです。

一般に、フレームワーク内の型の大部分は、クラスであるべきです。ただし、状況によっては値型の特性により構造体を使用する方が適切な場合もあります。

**✓** ある型のインスタンスは小さく、一般的に有効期間が短いかその他のオブジェクトに埋め込まれるのであれば、クラスの代わりに構造体を定義することを**考慮してください。**

**X** 次の条件をすべて満たさない限り、構造体を**定義しないでください。**

-   プリミティブ型 (`int`、`double`など) のように、論理的に 1 つの値を表す。

-   インスタンスのサイズは 16 バイト未満である。

-   変更不可である。

-   頻繁にボックス化することはない。

他のすべてのケースでは、クラスとして、型を定義する必要があります。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*

## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
