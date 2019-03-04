---
title: ジェネリックの利点 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
ms.openlocfilehash: 7f882bcdf5c1d9b8c81531c0fe37a3ee27c2e3a0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965412"
---
# <a name="benefits-of-generics-c-programming-guide"></a>ジェネリックの利点 (C# プログラミング ガイド)
ジェネリックを使用することによって、汎用基本データ型 <xref:System.Object> との値で型をキャストして一般化を行う、共通言語ランタイムや C# 言語の以前のバージョンの制限を解決できます。 ジェネリック クラスを作成すると、コンパイル時にタイプ セーフなコレクションを作成できます。  
  
 ジェネリック以外のコレクション クラスを使用する際の制限は、.NET クラス ライブラリの <xref:System.Collections.ArrayList> コレクション クラスを使用する短いプログラムを作成してみるとわかります。 <xref:System.Collections.ArrayList> クラスのインスタンスでは、任意の参照または値の型を格納できます。  
  
 [!code-csharp[csProgGuideGenerics#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#4)]  
  
 ただし、この利便性の一方でマイナス面もあります。 <xref:System.Collections.ArrayList> に追加される参照型や値型は暗黙的に <xref:System.Object> にアップキャストされます。 項目が値型の場合は、リストに追加するときにボックス化し、取得するときにボックス化解除する必要があります。 キャスト操作も、ボックス化/ボックス化解除操作も、パフォーマンスに悪い影響を及ぼします。特に、ボックス化およびボックス化解除の影響は、大型のコレクションの反復処理が必要な場合に非常に大きくなります。  
  
 また、コンパイル時の型チェックがないという制限もあります。<xref:System.Collections.ArrayList> はすべてを <xref:System.Object> にキャストするため、コンパイル時にクライアント コードが次のような処理を行うのを防ぐことができません。  
  
 [!code-csharp[csProgGuideGenerics#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#5)]  
  
 異種コレクションを作成することは有効であり、意図的に行うこともありますが、その場合、文字列と `ints` を 1 つの <xref:System.Collections.ArrayList> に組み合わせると、プログラミング エラーになる可能性があります。このエラーは、実行時まで検出されません。  
  
 C# 言語のバージョン 1.0 および 1.1 では、.NET Framework 基本クラス ライブラリのコレクション クラスにおける一般化されたコードの問題は、独自の型に固有のコレクションを記述することによってのみ回避できました。 もちろん、このようなクラスは複数のデータ型で再利用できないため、一般化のメリットがなく、格納する型ごとにクラスを書き直す必要があります。  
  
 <xref:System.Collections.ArrayList> や他の同じようなクラスで実際に必要なのは、クライアント コードで、使用する特定のデータ型をインスタンスごとに指定する方法です。 このような方法があれば、<xref:System.Object> にアップキャストする必要性がなくなり、また、コンパイラが型チェックを実行することもできます。 言い換えれば、<xref:System.Collections.ArrayList> には型パラメーターが必要なのです。 これを実現するのがジェネリックです。 <xref:System.Collections.Generic> 名前空間のジェネリック <xref:System.Collections.Generic.List%601> コレクションでは、コレクションに項目を追加するという同じ操作が次のようになります。  
  
 [!code-csharp[csProgGuideGenerics#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#6)]  
  
 クライアント コードでは、<xref:System.Collections.ArrayList> と比較される <xref:System.Collections.Generic.List%601> と共に追加される構文は、宣言とインスタンス化での型引数だけです。 このようにコーディングは若干複雑になりますが、それと引き換えに、<xref:System.Collections.ArrayList> よりも安全であるだけでなく、特にリスト項目が値型のときには処理時間が大幅に短縮されるリストを作成できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic>
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
- [ジェネリック コレクションを使用する状況](../../../standard/collections/when-to-use-generic-collections.md)
- [コレクションに関するガイドライン](../../../standard/design-guidelines/guidelines-for-collections.md)
