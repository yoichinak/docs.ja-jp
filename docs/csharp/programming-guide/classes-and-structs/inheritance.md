---
title: 継承 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 3211a4741eb56ad9e138a848e52fabbc1d3daaeb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924466"
---
# <a name="inheritance-c-programming-guide"></a>継承 (C# プログラミング ガイド)

継承は、カプセル化およびポリモーフィズムと共に、オブジェクト指向プログラミングの主要な 3 つの特性の 1 つです。 継承を使用すると、他のクラスで定義されている動作を再利用、拡張、および変更する新しいクラスを作成できます。 メンバーが継承される側のクラスを "*基底クラス*" と呼び、メンバーを継承する側のクラスを "*派生クラス*" と呼びます。 派生クラスは、直接の基底クラスを 1 つだけ持つことができます。 ただし、継承は推移的です。 ClassC が ClassB から派生し、ClassB が ClassA から派生している場合、ClassC は ClassB と ClassA で宣言されたメンバーを継承します。  
  
> [!NOTE]
> 構造体では、継承がサポートされていませんが、インターフェイスを実装することはできます。 詳細については、「[インターフェイス](../interfaces/index.md)」を参照してください。  
  
 概念的には、派生クラスは基底クラスから特化したクラスです。 たとえば、基底クラス `Animal` がある場合、`Mammal` という名前の派生クラスと、`Reptile` という名前の別の派生クラスを持つことができます。 `Mammal` は `Animal` であり、`Reptile` も `Animal` ですが、各派生クラスは、基底クラスから別々の特殊化を表します。  
  
 クラスを別のクラスから派生するように定義すると、派生クラスには、コンストラクターとファイナライザーを除く、基底クラスのすべてのメンバーが暗黙的に引き継がれます。 そのため、派生クラスでは、基底クラスのコードを再実装しなくても再利用できます。 派生クラスには、メンバーを追加できます。 このような方法で、派生クラスは基底クラスの機能を拡張します。  
  
 次の図は、あるビジネス プロセスの作業項目を表す `WorkItem` クラスを示しています。 他のすべてのクラスと同様に、<xref:System.Object?displayProperty=nameWithType> から派生し、そのすべてのメソッドを継承します。 `WorkItem` には、独自のメンバーが 5 つ追加されています。 これにはコンストラクターが含まれています。コンストラクターは継承されないためです。 `WorkItem` から継承される `ChangeRequest` クラスは、特定の種類の作業項目を表します。 `ChangeRequest` には、`WorkItem` と <xref:System.Object> から継承したメンバーに 2 つのメンバーが追加されます。 独自のコンストラクターを追加する必要があるほか、さらに `originalItemID` も追加されます。 `originalItemID` プロパティを使用すると、`ChangeRequest` インスタンスは、変更要求が適用される元の `WorkItem` と関連付けることができます。  
  
 ![クラスの継承を示す図](./media/inheritance/class-inheritance-diagram.png)  
  
 次の例は、前の図に示したクラスの関係が C# でどのように表現されるかを示しています。 また、`WorkItem` が仮想メソッド <xref:System.Object.ToString%2A?displayProperty=nameWithType> をオーバーライドする方法と、`ChangeRequest` クラスが `WorkItem` によるメソッドの実装を継承する方法も示しています。  
  
 [!code-csharp[csProgGuideInheritance#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#49)]  
  
## <a name="abstract-and-virtual-methods"></a>抽象メソッドと仮想メソッド  
 基底クラスでメソッドを [virtual](../../language-reference/keywords/virtual.md) として宣言する場合、派生クラスはそのメソッドを独自の実装で[オーバーライド](../../language-reference/keywords/override.md)することができます。 基底クラスでメンバーを [abstract](../../language-reference/keywords/abstract.md) として宣言する場合、そのクラスから直接継承される非抽象クラスで、そのメソッドをオーバーライドする必要があります。 派生クラス自体が抽象クラスである場合は、抽象メンバーを実装することなく継承します。 抽象メンバーと仮想メンバーは、オブジェクト指向プログラミングの重要な特性の 2 つ目であるポリモーフィズムの基礎です。 詳細については、「[ポリモーフィズム](./polymorphism.md)」を参照してください。  
  
## <a name="abstract-base-classes"></a>抽象基本クラス  
 [new](../../language-reference/operators/new-operator.md) 演算子を使用して直接インスタンス化されないようにする場合は、クラスを [abstract](../../language-reference/keywords/abstract.md) として宣言できます。 このようにすると、そのクラスは、新しいクラスを派生させないと使用できません。 抽象クラスには、それ自体が abstract として宣言された 1 つ以上のメソッド シグネチャを含めることができます。 これらのシグネチャは、パラメーターと戻り値を指定しますが、実装 (メソッドの本体) は持ちません。 抽象クラスには、抽象メンバーを含める必要はありません。ただし、クラスに抽象メンバーが含まれている場合は、クラス自体を抽象クラスとして宣言する必要があります。 抽象クラスでない派生クラスは、抽象基底クラスから継承した抽象メソッドすべてを実装する必要があります。 詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](./abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
## <a name="interfaces"></a>インターフェイス  
 "*インターフェイス*" は、抽象メンバーのみで構成される抽象基底クラスに類似した参照型です。 クラスでインターフェイスを実装するときは、インターフェイスのすべてのメンバーを実装する必要があります。 クラスは、直接的には 1 つの基底クラスからしか派生できませんが、複数のインターフェイスを実装できます。  
  
 インターフェイスは、必ずしも "is a" 関係を持たないクラスの特定の機能を定義するために使用されます。 たとえば、ある型の 2 つのオブジェクトが等しいかどうかをクライアント コードで判別できるようにする (ただし、等価性の定義は型によって行う) クラスまたは構造体では、<xref:System.IEquatable%601?displayProperty=nameWithType> インターフェイスを実装できます。 <xref:System.IEquatable%601> は、基底クラスと派生クラス間に存在する "is a" 関係 ("`Mammal` は `Animal` である" など) と同様の意味を示すものではありません。 詳細については、「[インターフェイス](../interfaces/index.md)」を参照してください。  
  
## <a name="preventing-further-derivation"></a>それ以上の派生の禁止  
 クラス自体またはメンバーを [sealed](../../language-reference/keywords/sealed.md)と宣言することにより、他のクラスがそのクラスまたはそのクラスのメンバーを継承できないようにすることができます。 詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](./abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
## <a name="derived-class-hiding-of-base-class-members"></a>派生クラスによる基底クラスのメンバーの隠ぺい  
 派生クラスは、同じ名前とシグネチャでメンバーを宣言することで、基底クラスのメンバーを隠ぺいすることができます。 [new](../../language-reference/keywords/new-modifier.md) 修飾子を使用すると、そのメンバーが基底クラスのメンバーのオーバーライドとして用意されているのではないことを明示的に指定できます。 [new](../../language-reference/keywords/new-modifier.md) の使用は必須ではありませんが、[new](../../language-reference/keywords/new-modifier.md) が使用されていない場合はコンパイラの警告が生成されます。 詳細については、「[Override キーワードと New キーワードによるバージョン管理](./versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](./knowing-when-to-use-override-and-new-keywords.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [クラスと構造体](./index.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/keywords/struct.md)
