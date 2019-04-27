---
title: 複合データ型 (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: ea719b60a6bcd40494666d4923fad296a8ddae70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907388"
---
# <a name="composite-data-types-visual-basic"></a>複合データ型 (Visual Basic)
Visual Basic に用意されている基本データ型だけでなくを作成するさまざまな種類の項目をアセンブルすることができますも*複合データ型*構造体、配列、およびクラスなどです。 基本型およびその他の複合型からは、複合データ型を構築できます。 たとえば、配列のメンバーを持つ構造体または構造体の要素の配列を定義できます。  
  
## <a name="data-types"></a>データの種類  
 複合型は、そのコンポーネントのいずれかのデータ型と異なります。 たとえば、配列の`Integer`の要素ではありません、`Integer`データ型。  
  
 配列のデータ型は、通常、必要に応じて、要素の型、かっこ、およびコンマを使用して表されます。 たとえば、1 次元配列`String`として表される要素`String()`との 2 次元配列`Boolean`として表される要素`Boolean(,)`。  
  
## <a name="structure-types"></a>構造体の型  
 すべての構造を構成する 1 つのデータ型はありません。 代わりに、場合でも、2 つの構造が同じ順序で同一の要素を定義、構造体の各定義は、一意のデータ型を表します。 ただし、同じ構造の 2 つ以上のインスタンスを作成する場合は、Visual Basic は、同じデータ型のそれらと見なします。  
  
## <a name="tuples"></a>タプル

タプルは、定義済みの型を持つ 2 つ以上のフィールドを含む軽量な構造です。 タプルは、Visual Basic 2017 以降ではサポートされています。 タプルは、参照渡しで引数を渡さずにまたはよりヘビーウェイトなクラスまたは構造体で返されるフィールドをパッケージ化せず、1 つのメソッドの呼び出しから複数の値を返す最もよく使用されます。 参照してください、[組](tuples.md)タプルの詳細についてはトピック。

## <a name="array-types"></a>配列型  
 すべてのアレイを構成する 1 つのデータ型はありません。 配列の特定のインスタンスのデータ型は、次のように決定されます。  
  
-   配列であること  
  
-   配列のランク (次元数)  
  
-   配列の要素型  
  
 具体的には、次元の長さはインスタンスのデータ型の一部ではありません。 次に例を示します。  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 前の例では、配列変数`arrayA`と`arrayB`、同じデータ型と見なされます: `Byte()` -場合でも、異なる長さに初期化されます。 変数`arrayB`と`arrayC`要素型が異なるために、同じ型のないです。 変数`arrayC`と`arrayD`ランクが異なるために、同じ型のないです。 変数`arrayD`と`arrayE`同じ型である — `Short(,)` : ランクと要素の型が同じため、たとえ`arrayD`がまだ初期化されていません。  
  
 配列の詳細については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
## <a name="class-types"></a>クラスの種類  
 すべてのクラスを構成する 1 つのデータ型はありません。 1 つのクラスは、別のクラスから継承できます、別のデータ型はそれぞれします。 同じクラスの複数のインスタンスでは、同じデータ型です。 クラスのインスタンスの 1 つの変数を割り当てるには別に、同じデータ型がだけでなく、メモリ内と同じクラスのインスタンスを指すようにします。  
  
 クラスの詳細については、次を参照してください。[オブジェクトとクラス](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)します。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [方法: 変数内で複数の値を保持する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
