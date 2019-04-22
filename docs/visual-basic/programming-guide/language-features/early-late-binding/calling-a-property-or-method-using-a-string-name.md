---
title: 文字列名によるプロパティまたはメソッドの呼び出し (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: e267c0c4d1d3e8f986348863d933c984f686b33b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842643"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>文字列名によるプロパティまたはメソッドの呼び出し (Visual Basic)
ほとんどの場合は、デザイン時に、オブジェクトのメソッドとプロパティを検出し、それらを処理するコードを記述できます。 ただし、場合によっては可能性がありますいないオブジェクトのプロパティとメソッドを事前にわかって、またはプロパティを指定するか、実行時にメソッドを実行するエンドユーザーの有効化の柔軟性をするだけです。  
  
## <a name="callbyname-function"></a>CallByName 関数  
 たとえば、オペレーターを COM コンポーネントに渡すことによって、ユーザーが入力した式を評価するクライアント アプリケーションを検討してください。 新しい演算子を必要とするコンポーネントを新しい関数を常に追加するとします。 標準のオブジェクトへのアクセス方法を使用する場合は、再コンパイルし、新しい演算子を使用できるように、クライアント アプリケーションを再配布する必要があります。 これを回避するには、使用することができます、`CallByName`関数を文字列として、アプリケーションを変更することがなく、新しい演算子を渡します。  
  
 `CallByName`関数では、実行時にプロパティまたはメソッドを指定する文字列を使用することができます。 署名、`CallByName`関数に次のようになります。  
  
 *結果* = `CallByName`(*オブジェクト*、 *ProcedureName*、 *CallType*、*引数*())  
  
 最初の引数*オブジェクト*、に対して操作を実行するオブジェクトの名前を受け取ります。 *ProcedureName*引数には、呼び出されるメソッドまたはプロパティ プロシージャの名前を含む文字列。 *CallType*引数には、プロシージャを呼び出すの型を表す定数。 メソッド (`Microsoft.VisualBasic.CallType.Method`)、読み取りプロパティ (`Microsoft.VisualBasic.CallType.Get`)、またはプロパティの設定 (`Microsoft.VisualBasic.CallType.Set`)。 *引数*引数は省略可能な型の配列を受け取る`Object`プロシージャに引数を格納しています。  
  
 使用することができます`CallByName`が、現在のソリューションでのクラスは COM オブジェクトへのアクセスは使用ほとんどの場合からオブジェクトまたは[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリ。  
  
 という名前のクラスを格納するアセンブリへの参照を追加するとします`MathClass`、という名前の新しい関数を持つ`SquareRoot`次のコードに示すように、します。  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 アプリケーションでは、どのメソッドが呼び出されるコントロールとその引数をテキスト ボックス コントロールを使用できます。 たとえば場合、`TextBox1`評価される式が含まれていますと`TextBox2`は関数の名前を入力するために使用、することができますを使用して、次のコードを呼び出す、`SquareRoot`関数内の式で`TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 「64」に入力した場合`TextBox1`で"SquareRoot"`TextBox2`を呼び出して、`CallMath`プロシージャ、内の数値の平方根`TextBox1`が評価されます。 例のコードを呼び出す、 `SquareRoot` (必須の引数として評価される式を含む文字列を扱う) に機能し、「8」を返します`TextBox1`(の平方根 64)。 もちろん、ユーザーが入力に無効な文字列`TextBox2`文字列には、メソッドではなくプロパティの名前が含まれている場合は、メソッドがあるその他の必要な引数は、実行時エラーが発生します。 使用する場合は、堅牢なエラー処理コードを追加する必要が`CallByName`これらやその他のエラーを予測します。  
  
> [!NOTE]
>  中に、`CallByName`関数は、場合によっては便利なことがあります、パフォーマンスに与える影響に対するその有用性を比較検討する必要があります: を使用して`CallByName`プロシージャを呼び出すには、遅延バインディング呼び出しよりもわずかに遅くなります。 繰り返し呼び出されます、このようなループ内で関数を呼び出す場合`CallByName`パフォーマンスに深刻な影響があることができます。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [オブジェクトの型の決定](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
