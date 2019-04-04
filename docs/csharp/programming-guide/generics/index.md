---
title: ジェネリック - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 186c5bc91204770e636eed5c008db23b798b6880
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202159"
---
# <a name="generics-c-programming-guide"></a>ジェネリック (C# プログラミング ガイド)
ジェネリックは、バージョン 2.0 の C# 言語と共通言語ランタイム (CLR) に追加されたものです。 ジェネリックは、.NET Framework に型パラメーターという概念を導入します。型パラメーターを使用すると、クラスやメソッドがクライアント コードで宣言され、インスタンス化されるまで、1 つ以上の型の指定を遅延させるクラスとメソッドを設計できます。 たとえば、ジェネリック型パラメーター T を使用すると、次に示すようにランタイムのキャストやボックス化操作のコストやリスクを負わずに他のクライアント コードで使用できる単一のクラスを記述できます。  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  
  
## <a name="generics-overview"></a>ジェネリックの概要  
  
-   ジェネリック型は、コードの再利用、タイプ セーフ、およびパフォーマンスを最大化するために使用します。  
  
-   ジェネリックの最も一般的な用途は、コレクション クラスの作成です。  
  
-   .NET Framework クラス ライブラリには、複数の新しいジェネリック コレクション クラスが <xref:System.Collections.Generic> 名前空間に含まれています。 <xref:System.Collections> 名前空間の <xref:System.Collections.ArrayList> などのクラスの代わりとして、できる限りこれらを使用してください。  
  
-   独自のジェネリック インターフェイス、クラス、メソッド、イベントおよびデリゲートを作成することができます。  
  
-   ジェネリック クラスは、特定のデータ型のメソッドへのアクセスを有効にするように制限できます。  
  
-   ジェネリック データ型で使用される型に関する情報は、実行時にリフレクションを使用して取得できます。  
  
## <a name="related-sections"></a>関連項目  
 詳細情報  
  
-   [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [ジェネリックの利点](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [ジェネリック型パラメーター](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [ジェネリック インターフェイス](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [C++ テンプレートと C# ジェネリックの違い](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [ジェネリックとリフレクション](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 詳細については、「[C# 言語の仕様](~/_csharplang/spec/types.md#constructed-types)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic>
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [型](../../../csharp/programming-guide/types/index.md)
- [\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [.NET のジェネリック](../../../standard/generics/index.md)
