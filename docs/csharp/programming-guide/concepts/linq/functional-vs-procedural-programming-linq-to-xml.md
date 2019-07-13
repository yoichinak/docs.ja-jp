---
title: 関数型プログラミングと手続き型プログラミング (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 1f713e54cefed5b1fcf8c29cd88aa7587a737327
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486950"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>関数型プログラミングと手続き型プログラミング (LINQ to XML) (C#)
XML アプリケーションには、次のようにさまざまな種類があります。  
  
- ソース XML ドキュメントを受け取り、そのドキュメントとは構造の異なる新しい XML ドキュメントを生成するアプリケーション  
  
- ソース XML ドキュメントを受け取り、HTML や CSV テキスト ファイルなどのまったく異なる形式のドキュメントを生成するアプリケーション  
  
- ソース XML ドキュメントを受け取り、データベースにレコードを挿入するアプリケーション  
  
- データベースなどの別のソースからデータを受け取り、そのデータから XML ドキュメントを作成するアプリケーション  
  
 XML アプリケーションには他にも種類がありますが、上記のアプリケーションは XML プログラマが実装する必要がある代表的な機能です。  
  
 上記のすべてのアプリケーションで、開発者は 2 つの対照的な方法を使用できます。  
  
- 宣言型の方法を使用する関数型構築  
  
- プロシージャ コードを使用するメモリ内の XML ツリーの変更  
  
 LINQ to XML は両方の方法をサポートします。  
  
 関数型の方法を使用する場合は、ソース ドキュメントを受け取り、必要な構造を持つ完全に新しいドキュメントが生成される変換を記述します。  
  
 XML ツリーを直接変更する場合は、メモリ内の XML ツリーでノード間を移動し、必要に応じてノードを挿入、削除、変更します。  
  
 いずれの方法でも LINQ to XML を使用できます。 同じクラスを使用し、場合によっては同じメソッドを使用します。 ただし、2 つの方法の構造と目標はかなり異なります。 たとえば、これらの方法のうち、どちらのパフォーマンスが優れているか、また使用するメモリ量はどちらが多い (または少ない) かは、状況によって異なる場合があります。 また、どちらの方法が保守性に優れたコードをより簡単に記述し生成できるかも、状況によって異なります。  
  
 2 つの方法の違いについては、「[メモリ内の XML ツリーの変更と関数型構築の比較 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)」をご覧ください。  
  
 関数型変換の記述に関するチュートリアルについては、「[XML の純粋関数型変換 (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- [LINQ to XML プログラミングの概要 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)
