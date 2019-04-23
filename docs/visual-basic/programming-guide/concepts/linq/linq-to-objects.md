---
title: LINQ to Objects (Visual Basic)
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: c1e2e8fbaaf984fec69322a459fc7c55890965ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326880"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
"LINQ to Objects" という用語は、[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) や [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) などの中間 LINQ プロバイダーまたは API を使用せずに、LINQ クエリを任意の <xref:System.Collections.IEnumerable> コレクションまたは <xref:System.Collections.Generic.IEnumerable%601> コレクションと直接組み合わせて使用することを意味します。 LINQ を使用して、<xref:System.Collections.Generic.List%601>、<xref:System.Array>、<xref:System.Collections.Generic.Dictionary%602> などの任意の列挙可能なコレクションを照会できます。 このコレクションは、ユーザー定義のコレクションでも、.NET Framework API から返されたコレクションでもかまいません。  
  
 本質的に、LINQ to Objects は、コレクションを扱うための新しい方法です。 従来の方法では、複雑な `For Each` ループを記述して、コレクションからデータを取得する方法を指定する必要がありました。 LINQ を使用する場合は、何を取得するかを表す宣言コードを記述します。  
  
 また、LINQ クエリには、従来の `For Each` ループと比べて、次の 3 つの重要な利点があります。  
  
1. 簡潔で読みやすい (特に複数の条件をフィルター処理する場合)。  
  
2. 強力なフィルター処理、並べ替え、およびグループ化機能を最小限のアプリケーション コードで実現できる。  
  
3. ほとんど、またはまったく変更せずに、他のデータ ソースに移植できる。  
  
 通常、データに対して実行する操作が複雑なほど、従来の反復処理手法の代わりに LINQ を使用する利便性が高くなります。  
  
 このセクションでは、いくつか例を挙げながら、LINQ を使った方法を具体的に説明します。 ただし、すべてを網羅したものではありません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 LINQ を使用して、文字列および文字列のコレクションの照会と変換を行う方法について説明します。 これらの基本原則を具体的に示すトピックへのリンクも含まれます。  
  
 [LINQ とリフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 LINQ でリフレクションを使用する方法を示すサンプルへのリンクを示します。  
  
 [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 LINQ を使用して、ファイル システムとやり取りする方法について説明します。 これらの概念を具体的に示すトピックへのリンクも含まれます。  
  
 [方法: ArrayList を照会する linq (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 C# で ArrayList を照会する方法を示します。  
  
 [方法: LINQ クエリ (Visual Basic) のカスタム メソッドを追加します。](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加して、LINQ クエリに使用できるメソッド セットを拡張する方法について説明します。  
  
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 LINQ について説明しているトピックへのリンクと、クエリを実行するコードの例を示します。
