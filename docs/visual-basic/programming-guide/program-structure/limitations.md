---
title: Visual Basic の制限事項
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 9fa0844f4508906ae30b936e41fb4392b74d1437
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648732"
---
# <a name="visual-basic-limitations"></a>Visual Basic の制限事項
以前のバージョンの Visual Basic では、変数名、モジュール、およびモジュールのサイズで許可されている変数の数の長さなど、コード内の境界を適用します。 Visual Basic .net では、これらの制限が緩和されました、書き込みと、コードを配置をより自由を与えます。  
  
 物理的な制限は、実行時メモリよりもよりするコンパイル時の考慮事項に依存します。 お勧めのプログラミング手法を使用して大規模なアプリケーションを複数のクラスとモジュールに分割する場合は、内部の Visual Basic の制限が発生する可能性はほとんど。  
  
 次に、極端なケースで発生する可能性のあるいくつかの制限を示します。  
  
- **名の長さ。** すべての宣言されたプログラミング要素の名前の文字の最大数です。 この最大値は、要素名が修飾されている場合に、全体の修飾文字列に適用されます。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
- **行の長さ。** 最大 65535 文字でソース コードの物理的な行があります。 論理ソース コード行は行継続文字を使用する場合は、長くすることはできます。 「[方法:分割および連結コード内でステートメント](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)します。  
  
- **配列の次元。** これは、配列に対して宣言できるディメンションの最大数です。 これにより、インデックスの配列要素を指定する際の数が制限されます。 参照してください[Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)します。  
  
- **文字列の長さ。** これは、1 つの文字列に格納できる Unicode 文字の最大数です。 参照してください[文字列データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)します。  
  
- **環境文字列の長さ。** コマンドライン引数として使用される任意の環境文字列の 32768 文字の最大値があります。 これは、すべてのプラットフォームでの制限です。  
  
## <a name="see-also"></a>関連項目

- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
