---
title: Visual Basic の名前付け規則
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 46f59403feced4baafef4662065cb7daedbeaa7b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837079"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic の名前付け規則
Visual Basic アプリケーションの要素に名前を付けるときは、その名前の最初の文字は、英字またはアンダー スコアにする必要があります。 ただし、アンダー スコアで始まる名前は[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS)に準拠しません。  
  
 次の提案が、名前付けに適用されます。  
  
-   名前の中のそれぞれの各単語を大文字で始めます。たとえば`FindLastRecord`や`RedrawMyForm`のようにします。  
  
-   関数やメソッド名は動詞で始めます。たとえば`InitNameArray`または`CloseDialog`のようにします。  
  
-   クラス、構造体、モジュールやプロパティ名は名詞で始めます。たとえば`EmployeeName`または`CarAccessory`のようにします。  
  
-   インターフェイス名はプレフィックス"I"を付けて始め、後に名詞または名詞句を続けます。 たとえば`IComponent`のようにします。 またはインターフェイスの動作を説明するような形容詞を付けます。 たとえば`IPersistable`のようにです。 アンダー スコアは使用しないで、略語の使用も控えてください。 なぜなら略語は混乱を招くからです。   
  
-    イベント ハンドラー名はイベントの種類を説明する名詞で始め、後に`EventHandler`サフィックスを続けます。 たとえば`MouseEventHandler`のようにします。   
  
-   `EventArgs`サフィックスを、イベント引数クラスの名前の中に含めます。  
  
-   イベントが"before"または"after"の概念を持つ時は、現在時制または過去時制のサフィックスを使います。 たとえば`ControlAdd`または`ControlAdded`のようにします。  
  
-   長い、または頻繁に使用される用語では、名前の長さを適切に維持するために略語を使用します。 たとえば、"Hypertext Markup Language"の代わりに"HTML"を使用します。 一般的に、32 文字を超える変数の名前は低解像度のモニターでは読むことが困難です。 また、略語はアプリケーション全体を通して一貫性のあるようにしてください。 プロジェクトの中で"HTML"と"Hypertext Markup Language"をランダムに切り替えることは混乱を招く可能性があります。   
  
-    外部スコープで使われている名前と同じものを、内部スコープの中で使用することは避けてください。 誤った変数がアクセスされた場合エラーが発生する可能性があります。 同名のキーワードと変数の間でコンフリクトが起きる場合、適切な種類のライブラリを使って先立ってキーワードを識別しなければなりません。 たとえば、`Date`という名前の変数がある場合、 <xref:System.DateTime.Date%2A?displayProperty=nameWithType>を呼ぶことによってのみ組み込み`Date`関数を使用することができます。   
  
## <a name="see-also"></a>関連項目

- [コード内の要素名としてのキーワード](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic の言語リファレンス](../../../visual-basic/language-reference/index.md)
