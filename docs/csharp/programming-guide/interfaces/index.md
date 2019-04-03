---
title: 'インターフェイス - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
  - 'interfaces [C#]'
  - 'C# language, interfaces'
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
---
# <a name="interfaces-c-programming-guide"></a>インターフェイス (C# プログラミング ガイド)

インターフェイスには、[クラス](../../language-reference/keywords/class.md)または[構造体](../../language-reference/keywords/struct.md)で実装できる関連機能のグループの定義が含まれます。
  
インターフェイスを使用すると、たとえば、クラス内の複数のソースからの動作を含めることができます。 C# ではクラスの複数の継承がサポートされないため、この機能は重要です。 また、構造体の継承をシミュレートする場合はインターフェイスを使用する必要があります。これは、実際に別の構造体またはクラスから継承することができないためです。  
  
[interface](../../language-reference/keywords/interface.md) キーワードを使用してインターフェイスを定義します。 次の例のようにします。  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

構造体の名前を、有効な C# の[識別子名](../inside-a-program/identifier-names.md)にする必要があります。 慣例により、インターフェイス名は大文字の `I` で始めます。

<xref:System.IEquatable%601> インターフェイスを実装するすべてのクラスまたは構造体は、インターフェイスで指定されたシグネチャに一致する <xref:System.IEquatable%601.Equals%2A> メソッドの定義を含む必要があります。 したがって、`IEquatable<T>` を実装するクラスが `Equals` メソッドを含むと想定したうえで、これを使用してクラスの 1 つのインスタンスが同じクラスの別のインスタンスと等しいかどうかを判定できます。  
  
`IEquatable<T>` の定義は `Equals` の実装を提供しません。 インターフェイスは、シグネチャのみを定義します。 つまり、C# のインターフェイスは、すべてのメソッドが抽象的である抽象クラスに似ています。 クラスまたは構造体は複数のインターフェイスを実装できます。ただし、クラスが継承できるのは、抽象的かどうかに関係なく、1 つのクラスのみです。
  
抽象クラスの詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
インターフェイスには、メソッド、プロパティ、イベント、インデクサー、またはこれらの 4 種類のメンバーの任意の組み合わせを含めることができます。 例へのリンクについては、「[関連項目](../interfaces/index.md#BKMK_RelatedSections)」を参照してください。 インターフェイスには、定数、フィールド、演算子、インスタンス コンストラクター、ファイナライザー、または型を含めることはできません。 インターフェイスのメンバーは、自動的にパブリックに設定され、アクセス修飾子を含むことはできません。 メンバーを [static](../../language-reference/keywords/static.md) として宣言することもできません。  
  
インターフェイスのメンバーを実装するには、実装するクラスの対応するメンバーがパブリックかつ非静的であり、インターフェイスのメンバーと同じ名前および署名を持つ必要があります。  
  
クラスまたは構造体でインターフェイスを実装するときは、インターフェイスで定義されているすべてのメンバーの実装を提供する必要があります。 インターフェイス自体は、基本クラスの機能を継承できるようにクラスまたは構造体が継承できる機能を提供しません。 ただし、基本クラスでインターフェイスが実装される場合、その基本クラスから派生するすべてのクラスはその実装を継承します。  
  
<xref:System.IEquatable%601> インターフェイスを実装する例を次に示します。 実装するクラスの `Car` は、<xref:System.IEquatable%601.Equals%2A> メソッドの実装を提供する必要があります。  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
クラスのプロパティとインデクサーでは、インターフェイスに定義されているプロパティまたはインデクサーの追加のアクセサーを定義できます。 たとえば、インターフェイスで [get](../../language-reference/keywords/get.md) アクセサーを持つプロパティを宣言するとします。 このインターフェイスを実装するクラスでは、`get` アクセサーと [set](../../language-reference/keywords/set.md) アクセサーの両方を持つ同じプロパティを宣言できます。 ただし、プロパティまたはインデクサーで明示的な実装を使用する場合は、これらのアクセサーが一致する必要があります。 明示的な実装の詳細については、「[明示的なインターフェイス実装](explicit-interface-implementation.md)」および「[インターフェイスのプロパティ](../classes-and-structs/interface-properties.md)」を参照してください。  

インターフェイスは、他のインターフェイスから継承できます。 クラスは、継承する基底クラス、または他のインターフェイスが継承するインターフェイスを介して、インターフェイスを複数回含めることができます。 ただし、クラスでインターフェイスの実装を提供できるのは 1 回のみであり、それもクラスでクラスの定義の一部としてインターフェイスを宣言する場合 (`class ClassName : InterfaceName`) に限られます。 インターフェイスを実装する基本クラスを継承することによってインターフェイスを継承する場合、基本クラスは、そのインターフェイスのメンバーの実装を提供します。 ただし、派生クラスでは、継承された実装を使用する代わりに、任意の仮想インターフェイスのメンバーを再実装できます。  
  
また、基本クラスでは、仮想メンバーを使用して、インターフェイスのメンバーを実装することもできます。 その場合、派生クラスでは、仮想メンバーをオーバーライドすることでインターフェイスの動作を変更できます。 仮想メンバーの詳細については、「[ポリモーフィズム](../classes-and-structs/polymorphism.md)」を参照してください。  
  
## <a name="interfaces-summary"></a>インターフェイスの概要

インターフェイスは、次の特性を持ちます。  

- インターフェイスは、抽象メンバーのみを含む抽象基本クラスに似ています。 インターフェイスを実装するすべてのクラスまたは構造体では、そのすべてのメンバーを実装する必要があります。
- インターフェイスを直接インスタンス化することはできません。 そのメンバーは、インターフェイスを実装する任意のクラスまたは構造体によって実装されます。
- インターフェイスには、イベント、インデクサー、メソッド、およびプロパティを含めることができます。
- インターフェイスには、メソッドの実装は含まれません。
- クラスまたは構造体は、複数のインターフェイスを実装できます。 クラスは、基本クラスを継承する一方で、1 つまたは複数のインターフェイスを実装できます。

## <a name="in-this-section"></a>このセクションの内容

[明示的なインターフェイスの実装](explicit-interface-implementation.md)  
 インターフェイスに固有のクラス メンバーを作成する方法について説明します。  
  
 [方法: インターフェイス メンバーを明示的に実装する](how-to-explicitly-implement-interface-members.md)  
 インターフェイスのメンバーを明示的に実装する方法の例を示します。  
  
 [方法: 2 つのインターフェイスのメンバーを明示的に実装する](how-to-explicitly-implement-members-of-two-interfaces.md)  
 継承を持つインターフェイスのメンバーを明示的に実装する方法の例を示します。  
  
## <a name="BKMK_RelatedSections"></a>関連項目

- [インターフェイスのプロパティ](../classes-and-structs/interface-properties.md)  
- [インターフェイスのインデクサー](../indexers/indexers-in-interfaces.md)  
- [方法: インターフェイス イベントを実装する](../events/how-to-implement-interface-events.md)  
- [クラスと構造体](../classes-and-structs/index.md)  
- [継承](../classes-and-structs/inheritance.md)  
- [メソッド](../classes-and-structs/methods.md)  
- [ポリモーフィズム](../classes-and-structs/polymorphism.md)  
- [抽象クラスとシール クラス、およびクラス メンバー](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [プロパティ](../classes-and-structs/properties.md)  
- [イベント](../events/index.md)  
- [インデクサー](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>参考書籍の該当する章

「[インターフェイス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29)」(『[Learning C# 3.0: Master the fundamentals of C# 3.0 (C# 3.0 の学習: C# 3.0 の基礎を習得)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)』)

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [継承](../classes-and-structs/inheritance.md)
- [識別子名](../inside-a-program/identifier-names.md)
