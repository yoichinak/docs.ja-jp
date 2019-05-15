---
title: ジェネリックの概要 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: 0d7ecb7f7fd0bb0985234cdc2cf8d37b53323c86
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595486"
---
# <a name="introduction-to-generics-c-programming-guide"></a>ジェネリックの概要 (C# プログラミング ガイド)
ジェネリックのクラスとメソッドは、非ジェネリックでは不可能な方法で、再利用性、タイプ セーフ、効率性を同時に実現しています。 ジェネリックは、コレクションとそれを操作するメソッドとともに使用されるのが通常です。 .NET Framework クラス ライブラリのバージョン 2.0 には、いくつかの新しいジェネリック ベースのコレクション クラスを含む新しい名前空間、<xref:System.Collections.Generic> が用意されています。 .NET Framework 2.0 以降を対象とするすべてのアプリケーションでは、<xref:System.Collections.ArrayList> などの以前の非ジェネリック コレクション クラスの代わりに、新しいジェネリック コレクション クラスを使用することをお勧めします。 詳細については、「[.NET のジェネリック](../../../standard/generics/index.md)」を参照してください。  
  
 もちろん、カスタムのジェネリック型やジェネリック メソッドを作成して、タイプ セーフで効率的な独自の汎用ソリューションや設計パターンを実現することもできます。 次のコード例では、デモンストレーション用の簡単なジェネリックのリンク リスト クラスを示します。 (通常は、独自のクラスを作成するのではなく、.NET Framework クラス ライブラリに用意されている <xref:System.Collections.Generic.List%601> クラスを使用してください。)この例では、通常、具体的な型を使用して、リストに格納する項目の型を示す場面で、型パラメーター `T` を使用しています。 このパラメーターは、次のように使用されています。  
  
- `AddHead` メソッドのメソッド パラメーターの型として使用。  
  
- 入れ子になった `Node` クラスの `Data` プロパティの戻り値の型として使用。  
  
- 入れ子になったクラスのプライベート メンバー `data` の型として使用。  
  
 T は、入れ子になった `Node` クラスで使用できることに注意してください。 `GenericList<T>` が `GenericList<int>` のような具象型でインスタンス化されると、`T` の部分はそれぞれ `int` に置き換えられます。  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 次のコード例では、クライアント コードでジェネリックの `GenericList<T>` クラスを使用して、整数のリストを作成する方法を示しています。 このコードの型引数を変更するだけで、文字列やその他の任意のカスタム型のリストを作成するように簡単に修正できます。  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic>
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ジェネリック](../../../csharp/programming-guide/generics/index.md)
