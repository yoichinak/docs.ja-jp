---
title: '方法: オブジェクト初期化子 (Visual Basic) を使用してオブジェクトを宣言します。'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 314706207800b2e86aa0032a52d8c50fbb726887
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825137"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>方法: オブジェクト初期化子 (Visual Basic) を使用してオブジェクトを宣言します。
オブジェクト初期化子を使用すると、宣言および 1 つのステートメント内のクラスのインスタンスをインスタンス化できます。 さらに、パラメーター化されたコンス トラクターを呼び出さずに、同時インスタンスの 1 つまたは複数のメンバーを初期化できます。  
  
 名前付きの型のインスタンスを作成する、オブジェクト初期化子を使用すると、指定した順序で指定されたメンバーの初期化後に、クラスの既定のコンス トラクターが呼び出されます。  
  
 インスタンスを作成する方法は、次の手順を`Student`3 つの異なる方法でクラス。 クラスには、名、姓、名、およびその他のクラスの年プロパティがあります。 新しいインスタンスを作成、3 つの宣言の各`Student`、プロパティを持つ`First`プロパティ「マイケル ・」に設定`Last`「tucker です」に設定され、その他のすべてのメンバーが既定値に設定します。 手順では、各宣言の結果は、次の例は、オブジェクト初期化子を使用しないのと同じです。  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 実装については、`Student`クラスを参照してください[方法。項目の一覧を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)です。 コードをコピーするには、クラスを設定しの一覧を作成するには、そのトピックから`Student`オブジェクトを使用します。  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>オブジェクト初期化子を使用して名前付きクラスのオブジェクトを作成するには  
  
1.  コンス トラクターを使用する場合、宣言を開始します。  
  
     `Dim student1 As New Student`  
  
2.  キーワードを入力`With`、初期化リストを中かっこでその後にします。  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  初期化リストで初期化し、初期値を割り当てるしたい各プロパティが含まれます。 プロパティの名前の前にピリオドです。  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     クラスの 1 つまたは複数のメンバーを初期化することができます。  
  
4.  または、クラスの新しいインスタンスを宣言し、値を割り当てることができます。 インスタンスを最初に、宣言`Student`:  
  
     `Dim student2 As Student`  
  
5.  インスタンスの作成を開始`Student`通常どおりにします。  
  
     `Dim student2 As Student = New Student`  
  
6.  型`With`と 1 つまたは複数のメンバーの新しいインスタンスを初期化するためにオブジェクト初期化子、します。  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7.  省略すると、前の手順で定義を簡略化できます`As Student`します。 コンパイラが判断した場合、これを行うと、`student3`のインスタンスである`Student`ローカル型推論を使用しています。  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。  
  
## <a name="see-also"></a>関連項目

- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [方法: 項目の一覧を作成します。](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [オブジェクト初期化子:名前付きの匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
