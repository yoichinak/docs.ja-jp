---
title: 匿名メソッド - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: d7823611df5e02040fd8735e1fa6ea7841298836
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595048"
---
# <a name="anonymous-methods-c-programming-guide"></a>匿名メソッド (C# プログラミング ガイド)
C# 2.0 より前のバージョンでは、[デリゲート](../../../csharp/language-reference/keywords/delegate.md)を宣言するには[名前付きメソッド](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)を使用するしかありませんでした。 C# 2.0 では匿名メソッドが導入され、C# 3.0 以降では、インライン コードを記述するための本来の方法として、匿名メソッドに代わってラムダ式が使用されるようになりました。 ただし、このトピックに記載した匿名メソッドに関する情報は、ラムダ式にも適用されます。 ラムダ式にはない機能を匿名メソッドが備えているケースが 1 つあります。 匿名メソッドではパラメーター リストを省略できます。 つまり、匿名メソッドを、さまざまなシグネチャを持つデリゲートに変換できます。 これはラムダ式では不可能です。 ラムダ式の詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。  
  
 匿名メソッドは、基本的にコード ブロックをデリゲート パラメーターとして渡すときに作成します。 2 つの例を挙げます。  
  
 [!code-csharp[csProgGuideDelegates#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#6)]  
  
 [!code-csharp[csProgGuideDelegates#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#5)]  
  
 匿名メソッドを使用すると、別のメソッドを作成する必要がないため、デリゲートをインスタンス化する際のコーディングのオーバーヘッドを削減できます。  
  
 たとえば、デリゲートの代わりにコード ブロックを指定すると、メソッドを作成するのが余分なオーバーヘッドと思われる場合に役立つことがあります。 新しいスレッドを開始する場合などがそのよい例です。 このクラスではスレッドを作成し、スレッドが実行するコードも含みますが、デリゲート用の追加のメソッドは作成していません。  
  
 [!code-csharp[csProgGuideDelegates#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#7)]  
  
## <a name="remarks"></a>解説  
 匿名メソッドのパラメーターのスコープは、"*匿名メソッド ブロック*" です。  
  
 匿名メソッド ブロックの内部で使用しているジャンプ ステートメント ([goto](../../../csharp/language-reference/keywords/goto.md)、[break](../../../csharp/language-reference/keywords/break.md)、[continue](../../../csharp/language-reference/keywords/continue.md) など) のジャンプ先がブロックの外部にある場合はエラーになります。 また、匿名メソッド ブロックの外部で使用しているジャンプ ステートメント (`goto`、`break`、`continue` など) のジャンプ先がブロックの内部にある場合もエラーになります。  
  
 匿名メソッドの宣言をスコープに含むローカル変数とパラメーターは、匿名メソッドの "*外部*" 変数と呼ばれます。 たとえば、次のコード セグメントに示されている `n` は外部変数です。  
  
 [!code-csharp[csProgGuideDelegates#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#8)]  
  
 外部変数 `n` への参照は、デリゲートの作成時に "*キャプチャ*" されるといわれます。 ローカル変数とは異なり、匿名メソッドを参照するデリゲートがガベージ コレクションの対象になるまで、キャプチャされた変数の有効期間を拡張します。  
  
 匿名メソッドは、外部スコープの [in](../../../csharp/language-reference/keywords/in.md)、[ref](../../../csharp/language-reference/keywords/ref.md)、[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) パラメーターにアクセスできません。  
  
 "*匿名メソッド ブロック*" 内のアンセーフ コードにはアクセスできません。  
  
 匿名メソッドは、[is](../../../csharp/language-reference/keywords/is.md) 演算子の左辺では使用できません。  
  
## <a name="example"></a>例  
 次の例は、デリゲートをインスタンス化する 2 つの方法を示しています。  
  
- デリゲートと匿名メソッドを関連付ける。  
  
- デリゲートと名前付きメソッド (`DoWork`) を関連付ける。  
  
 どちらの場合も、デリゲートを呼び出すと、メッセージが表示されます。  
  
 [!code-csharp[csProgGuideDelegates#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#4)]  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [デリゲート](../../../csharp/programming-guide/delegates/index.md)
- [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
