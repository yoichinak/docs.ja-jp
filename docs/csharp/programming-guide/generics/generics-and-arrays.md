---
title: ジェネリックと配列 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: fee66cf7bd0ab3c051ea67acc323efa02a21a017
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659792"
---
# <a name="generics-and-arrays-c-programming-guide"></a>ジェネリックと配列 (C# プログラミング ガイド)
C# 2.0 以降、下限が 0 の一次元配列は自動的に <xref:System.Collections.Generic.IList%601> を実装します。 これにより、同じコードで配列や他のコレクション型を反復処理できるジェネリック メソッドを作成できます。 この手法は主に、コレクションのデータを読み込むときに便利です。 <xref:System.Collections.Generic.IList%601> インターフェイスを使用して配列の要素を追加したり、削除したりすることはできません。 このコンテキストの配列で、<xref:System.Collections.Generic.IList%601.RemoveAt%2A> のような、<xref:System.Collections.Generic.IList%601> メソッドを呼び出そうとすると、例外がスローされます。  
  
 次のコード例からは、<xref:System.Collections.Generic.IList%601> 入力パラメーターを受け取る単一のジェネリック メソッドがリストと配列 (この例では、整数の配列) の両方を反復処理できることがわかります。  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic>
- [C# プログラミング ガイド](../index.md)
- [ジェネリック](./index.md)
- [配列](../arrays/index.md)
- [ジェネリック](../../../standard/generics/index.md)
