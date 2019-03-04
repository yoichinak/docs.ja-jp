---
title: ジェネリック型の型パラメーター - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: f6acbfee5c6b5ec426076d7bf766a3c6894b736f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972184"
---
# <a name="generic-type-parameters-c-programming-guide"></a>ジェネリック型の型パラメーター (C# プログラミング ガイド)
ジェネリック型またはメソッド定義で、型パラメーターは、ジェネリック型の変数をインスタンス化するときにクライアントが指定する特定の型のためのプレースホルダーになります。 「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」に記載されている `GenericList<T>` などのジェネリック クラスは、実際は型でないため、そのままでは使用できません。これは型の設計図のようなものです。 `GenericList<T>` を使用するには、クライアント コードで構築された型を宣言し、インスタンス化する必要があります。山かっこ内に型引数を指定します。 この特定のクラスの型引数は、コンパイラで認識されるあらゆる型にすることができます。 構築された型インスタンスは、次のようにさまざまな型引数を利用し、いくつでも作成できます。  
  
 [!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
 `GenericList<T>` の各インスタンスでは、クラス内のすべての `T` は実行時に型引数に置換されます。 この置換を使用し、単一クラス定義を使用してタイプ セーフで効率的なオブジェクトを 3 つ作成しました。 この置換が CLR で実行されるしくみについては、「[ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)」を参照してください。  
  
## <a name="type-parameter-naming-guidelines"></a>型パラメーターの名前付けガイドライン  
  
-   1 文字の名前でも完全に説明され、説明的な名前を付けることに意味がない場合を除き、ジェネリック型パラメーターには**説明的な名前を付けてください**。  
  
     [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
-   1 文字の型パラメーターを持つ型の型パラメーター名として T を利用することを**検討してください**。  
  
     [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
-   型パラメーターの説明的な名前には "T" という**接頭辞を付けてください**。  
  
     [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
-   型パラメーターに与えられた制約をパラメーターの名前で示唆することを**検討してください**。 たとえば、`ISession` に制約されているパラメーターの名前を `TSession` にします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic>
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ジェネリック](../../../csharp/programming-guide/generics/index.md)
- [C++ テンプレートと C# ジェネリックの違い](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
