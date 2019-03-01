---
title: 部分メソッド (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 4b35985aa67cea7b58ddf05611cf4e0813a2d442
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977462"
---
# <a name="partial-methods-visual-basic"></a>部分メソッド (Visual Basic)
部分メソッドには、カスタム ロジックをコードに挿入する開発者が有効にします。 通常、コードには、デザイナーで生成されたクラスの一部です。 部分メソッドは、コード ジェネレーターによって作成される部分クラスで定義され、何かが変更されたことを通知によく使用されます。 これらの変更に対応するカスタム動作を指定する、開発者が有効にします。  
  
 コード ジェネレーターのデザイナーは、メソッドのシグネチャとメソッドに対する 1 つまたは複数の呼び出しを定義します。 開発者、生成されたコードの動作をカスタマイズする場合、メソッドの実装を用意できます。 実装を指定しない場合、メソッドの呼び出しは追加のパフォーマンスのオーバーヘッドなしでその結果、コンパイラによって削除されます。  
  
## <a name="declaration"></a>宣言  
 キーワードを配置することで、生成されたコードは部分メソッドの定義をマーク`Partial`署名行の先頭。  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 定義には、次の条件を満たす必要があります。  
  
-   メソッドである必要があります、`Sub`ではなく、`Function`します。  
  
-   メソッドの本体は空のままにする必要があります。  
  
-   アクセス修飾子がある必要があります`Private`します。  
  
## <a name="implementation"></a>実装  
 実装では、主に、部分メソッドの本文を入力します。 この実装は一般に、定義から別の部分クラスを生成されたコードを拡張する必要がある開発者によって書き込まれます。  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 前の例では、宣言内のシグネチャを正確には、重複するが、バリエーションが可能です。 具体的には、その他の修飾子を追加できるよう`Overloads`または`Overrides`します。 1 つだけ`Overrides`修飾子を使用します。 メソッドの修飾子の詳細については、次を参照してください。 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)します。  
  
## <a name="use"></a>使用  
 場合とその他の部分メソッドを呼び出す`Sub`プロシージャ。 メソッドが実装されている場合は、引数が評価され、メソッドの本体が実行されます。 ただし、部分メソッドの実装は省略可能です。 メソッドが実装されていない場合は、それへの呼び出しが効果を持たず、メソッドに引数として渡される式は評価されません。  
  
## <a name="example"></a>例  
 Product.Designer.vb という名前のファイル、定義、`Product`を持つクラス、`Quantity`プロパティ。  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 実装を提供 Product.vb という名前のファイル、`QuantityChanged`します。  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 最後に、プロジェクトの Main メソッドでは宣言を`Product`インスタンスし、指定の初期値をその`Quantity`プロパティ。  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 このメッセージを表示するメッセージ ボックスが表示する必要があります。  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>関連項目
- [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Sub プロシージャ](./sub-procedures.md)
- [省略可能なパラメーター](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [LINQ to SQL でのコード生成](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [部分メソッドによるビジネス ロジックの追加](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
