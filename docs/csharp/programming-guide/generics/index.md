---
title: ジェネリック - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: e32eb7c60e01ca72824ffb3a1e1269cf34650f5a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423392"
---
# <a name="generics-c-programming-guide"></a>ジェネリック (C# プログラミング ガイド)
ジェネリックは、バージョン 2.0 の C# 言語と共通言語ランタイム (CLR) に追加されたものです。 ジェネリックは、.NET Framework に型パラメーターという概念を導入します。型パラメーターを使用すると、クラスやメソッドがクライアント コードで宣言され、インスタンス化されるまで、1 つ以上の型の指定を遅延させるクラスとメソッドを設計できます。 たとえば、ジェネリック型パラメーター T を使用すると、次に示すようにランタイムのキャストやボックス化操作のコストやリスクを負わずに他のクライアント コードで使用できる単一のクラスを記述できます。  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

ジェネリックのクラスとメソッドは、非ジェネリックでは不可能な方法で、再利用性、タイプ セーフ、効率性を同時に実現しています。 ジェネリックは、コレクションとそれを操作するメソッドとともに使用されるのが通常です。 .NET Framework クラス ライブラリのバージョン 2.0 には、いくつかの新しいジェネリック ベースのコレクション クラスを含む新しい名前空間、<xref:System.Collections.Generic> が用意されています。 .NET Framework 2.0 以降を対象とするすべてのアプリケーションでは、<xref:System.Collections.ArrayList> などの以前の非ジェネリック コレクション クラスの代わりに、新しいジェネリック コレクション クラスを使用することをお勧めします。 詳細については、「[.NET のジェネリック](../../../standard/generics/index.md)」を参照してください。  
  
 もちろん、カスタムのジェネリック型やジェネリック メソッドを作成して、タイプ セーフで効率的な独自の汎用ソリューションや設計パターンを実現することもできます。 次のコード例では、デモンストレーション用の簡単なジェネリックのリンク リスト クラスを示します。 (通常は、独自のクラスを作成するのではなく、.NET Framework クラス ライブラリに用意されている <xref:System.Collections.Generic.List%601> クラスを使用してください。)この例では、通常、具体的な型を使用して、リストに格納する項目の型を示す場面で、型パラメーター `T` を使用しています。 このパラメーターは、次のように使用されています。  
  
- `AddHead` メソッドのメソッド パラメーターの型として使用。  
  
- 入れ子になった `Node` クラスの `Data` プロパティの戻り値の型として使用。  
  
- 入れ子になったクラスのプライベート メンバー `data` の型として使用。  
  
 T は、入れ子になった `Node` クラスで使用できることに注意してください。 `GenericList<T>` が `GenericList<int>` のような具象型でインスタンス化されると、`T` の部分はそれぞれ `int` に置き換えられます。  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 次のコード例では、クライアント コードでジェネリックの `GenericList<T>` クラスを使用して、整数のリストを作成する方法を示しています。 このコードの型引数を変更するだけで、文字列やその他の任意のカスタム型のリストを作成するように簡単に修正できます。  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a>ジェネリックの概要  
  
- ジェネリック型は、コードの再利用、タイプ セーフ、およびパフォーマンスを最大化するために使用します。  
  
- ジェネリックの最も一般的な用途は、コレクション クラスの作成です。  
  
- .NET Framework クラス ライブラリには、複数の新しいジェネリック コレクション クラスが <xref:System.Collections.Generic> 名前空間に含まれています。 <xref:System.Collections> 名前空間の <xref:System.Collections.ArrayList> などのクラスの代わりとして、できる限りこれらを使用してください。  
  
- 独自のジェネリック インターフェイス、クラス、メソッド、イベントおよびデリゲートを作成することができます。  
  
- ジェネリック クラスは、特定のデータ型のメソッドへのアクセスを有効にするように制限できます。  
  
- ジェネリック データ型で使用される型に関する情報は、実行時にリフレクションを使用して取得できます。  
  
## <a name="related-sections"></a>関連項目  
 詳細情報  
  
- [ジェネリック型パラメーター](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [ジェネリック インターフェイス](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [C++ テンプレートと C# ジェネリックの違い](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [ジェネリックとリフレクション](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 詳細については、「[C# 言語の仕様](~/_csharplang/spec/types.md#constructed-types)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic>
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [型](../../../csharp/programming-guide/types/index.md)
- [\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [.NET のジェネリック](../../../standard/generics/index.md)
