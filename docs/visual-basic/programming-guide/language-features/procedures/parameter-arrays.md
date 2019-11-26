---
title: パラメーター配列
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: ffb532fbac70b9aa8ab210450e4d9207f5e0291f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351124"
---
# <a name="parameter-arrays-visual-basic"></a>パラメーター配列 (Visual Basic)
Usually, you cannot call a procedure with more arguments than the procedure declaration specifies. When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter. You do not have to know the number of elements in the parameter array when you define the procedure. The array size is determined individually by each call to the procedure.  
  
## <a name="declaring-a-paramarray"></a>Declaring a ParamArray  
 You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list. 次の規則が適用されます。  
  
- A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.  
  
- The parameter array must be passed by value. It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.  
  
- The parameter array is automatically optional. Its default value is an empty one-dimensional array of the parameter array's element type.  
  
- All parameters preceding the parameter array must be required. The parameter array must be the only optional parameter.  
  
## <a name="calling-a-paramarray"></a>Calling a ParamArray  
 When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:  
  
- Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument. In this case, an empty array is passed to the procedure. If you explicitly pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, a null array is passed to the procedure and may result in a NullReferenceException if the called procedure does not check for this condition.
  
- A list of an arbitrary number of arguments, separated by commas. The data type of each argument must be implicitly convertible to the `ParamArray` element type.  
  
- An array with the same element type as the parameter array's element type.  
  
 In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.  
  
> [!IMPORTANT]
> Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application. If you accept a parameter array, you should test for the size of the array that the calling code passed to it. Take appropriate steps if it is too large for your application. 詳細については、「[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)」を参照してください。  
  
## <a name="example"></a>例  
 The following example defines and calls the function `calcSum`. The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [手順](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)
- [省略可能なパラメーター](./optional-parameters.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
