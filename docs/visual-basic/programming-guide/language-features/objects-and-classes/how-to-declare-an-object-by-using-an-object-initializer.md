---
title: '方法: オブジェクト初期化子を使用してオブジェクトを宣言する'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: ae04d338b61027c3917ad3a7f62ff40f0a95e53e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347137"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>方法: オブジェクト初期化子を使用してオブジェクトを宣言する (Visual Basic)
オブジェクト初期化子を使用すると、1 つのステートメントで、クラスのインスタンスを宣言してインスタンス化できます。 また、パラメーター化されたコンストラクターを呼び出さずに、インスタンスの 1 つ以上のメンバーを同時に初期化できます。  
  
 オブジェクト初期化子を使用して、名前付きの型のインスタンスを作成すると、クラスのパラメーターなしのコンストラクターが呼び出され、続いて指定した順番で、指定したメンバーの初期化が行われます。  
  
 次の手順は、3 つの異なる方法で `Student` クラスのインスタンスを作成する方法を示しています。 クラスには特に姓、名、および学年のプロパティがあります。 3 つの各宣言では、プロパティ `First` を "Michael" に設定し、プロパティ `Last` を "Tucker" に設定し、その他のすべてのメンバーをそれらの既定値に設定して、`Student` の新しいインスタンスを作成しています。 プロシージャ内の各宣言の結果は、オブジェクト初期化子を使用しない次の例と同じです。  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 `Student` クラスの実装については、「[方法:項目のリストを作成する](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)」を参照してください。 そのトピックからコードをコピーして、クラスを設定し、操作する `Student` オブジェクトの一覧を作成できます。  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>オブジェクト初期化子を使用して、名前付きクラスのオブジェクトを作成するには  
  
1. コンストラクターを使用することを計画した場合と同様に、宣言を開始します。  
  
     `Dim student1 As New Student`  
  
2. キーワード `With` の後に中かっこで囲んだ初期化リストを含めて入力します。  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. 初期化リストに、初期化して、それに初期値を代入する各プロパティを含めます。 プロパティの名前の前にピリオドを付けます。  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     クラスの 1 つ以上のメンバーを初期化できます。  
  
4. または、クラスの新しいインスタンスを宣言してから、それに値を代入することもできます。 まず、`Student` のインスタンスを宣言します。  
  
     `Dim student2 As Student`  
  
5. 通常の方法で `Student` のインスタンスの作成を開始します。  
  
     `Dim student2 As Student = New Student`  
  
6. `With` に続けてオブジェクト初期化子を入力して、新しいインスタンスの 1 つ以上のメンバーを初期化します。  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. `As Student` を省略すると、前のステップの定義を簡略化できます。 これを行うと、コンパイラによって、ローカル型推論を使用して、`student3` が `Student` のインスタンスであると判断されます。  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     詳細については、「[ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [方法: 項目のリストを作成する](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [オブジェクト初期化子: 名前付きの型と匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
