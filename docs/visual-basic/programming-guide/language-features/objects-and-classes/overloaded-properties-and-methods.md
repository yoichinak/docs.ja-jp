---
title: オーバー ロードされたプロパティとメソッド (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: 8d7341370d9770d2e57f786ac7c68277e66a9bbd
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677397"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>オーバー ロードされたプロパティとメソッド (Visual Basic)

オーバー ロードは、1 つ以上のプロシージャ、インスタンス コンス トラクターで異なる引数の型が同じ名前のクラスのプロパティの作成です。

## <a name="overloading-usage"></a>使用率をオーバー ロード

オーバー ロードは、オブジェクト モデルで、別のデータ型を操作する手順については、同じ名前を使用しているときに特に便利です。 たとえば、いくつかの異なるデータ型を表示できるクラスがある`Display`手順のようになります。

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

オーバー ロードが可能でない場合でも、次に示すように、同じよう各手順では、個別の名前を作成する必要は。

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

オーバー ロードすると、使用できるデータ型の選択肢を提供するために、プロパティまたはメソッドを使用しやすきます。 たとえば、オーバー ロード`Display`説明以前メソッドでは、次のコード行のいずれか。

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

実行時に、Visual Basic は、指定したパラメーターのデータ型に基づいて適切なプロシージャを呼び出します。

## <a name="overloading-rules"></a>オーバー ロードの規則

 クラスのオーバー ロードされたメンバーを作成するには、2 つ以上のプロパティまたは同じ名前のメソッドを追加します。 派生オーバー ロードされたメンバーを除く各オーバー ロードされたメンバーはパラメーター リストが異なっている必要があり、次の項目は、プロパティまたはプロシージャをオーバー ロードとの差別化機能として使用できません。

- 修飾子など`ByVal`または`ByRef`メンバー、またはメンバーのパラメーターに適用されています。

- パラメーターの名前

- プロシージャの戻り値の型

`Overloads`オーバー ロード、ときに、キーワードは省略可能ですが、メンバーを使用していずれかのオーバー ロードされた場合、`Overloads`このキーワードはキーワード、その他のすべてのオーバー ロードされたメンバーと同じ名前で指定もする必要があります。

派生クラスで継承されたメンバーを同じパラメーターおよびパラメーターの型と呼ばれるプロセスを持つメンバーをオーバー ロードできます*名前とシグネチャによるシャドウ*します。 場合、`Overloads`キーワードを使用して名前とシグネチャによるシャドウ、メンバーの派生クラスの実装が、基底クラスの実装ではなく使用され、そのメンバーの他のすべてのオーバー ロードのインスタンスで使用できるときに、派生クラスです。

場合、`Overloads`と同じパラメーターおよびパラメーターの型を持つメンバーを持つ継承されたメンバーをオーバー ロード時にキーワードを省略すると、オーバー ロードが呼び出されます*名前によるシャドウ*します。 継承されたメンバーの実装を置き換える名前によるシャドウおり、その他のすべてのオーバー ロードに置き換わります、派生クラスのインスタンスを使用できなくなります。

`Overloads`と`Shadows`修飾子両方では使用できません、同じプロパティまたはメソッドです。

### <a name="example"></a>例

次の例は、いずれかを受け取るオーバー ロードされたメソッドを作成、`String`または`Decimal`形式の金額と販売税を含む文字列を返します。

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>この例を使用して、オーバー ロードされたメソッドを作成するには

1. 新しいプロジェクトを開き、という名前のクラスを追加`TaxClass`します。

2. `TaxClass` クラスに次のコードを追加します。

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. フォームに次の手順を追加します。

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. 呼び出し、フォームにボタンを追加、`ShowTax`プロシージャから、`Button1_Click`ボタンのイベント。

5. プロジェクトを実行し、テスト、オーバー ロードされたフォーム上のボタンをクリックします。`ShowTax`プロシージャ。

実行時に、コンパイラは、使用されているパラメーターに一致する適切なオーバー ロードされた関数を選択します。 ボタンをクリックすると、オーバー ロードされたメソッドが呼び出された最初、`Price`パラメーターが文字列と、メッセージは、"価格は文字列です。 税金が $$5.12"が表示されます。 `TaxAmount` 呼び出すと、`Decimal`値を 2 回目と、メッセージ、"価格は 10 進数です。 税金が $$5.12"が表示されます。

## <a name="see-also"></a>関連項目

- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
