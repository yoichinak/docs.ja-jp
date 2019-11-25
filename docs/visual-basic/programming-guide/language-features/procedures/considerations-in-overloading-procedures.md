---
title: プロシージャのオーバーロードに関する注意事項
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: 4a0cfe176a59b3f90f5850ae8b4e34784c400c6b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351010"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>プロシージャのオーバーロードに関する注意事項 (Visual Basic)
When you overload a procedure, you must use a different *signature* for each overloaded version. This usually means each version must specify a different parameter list. For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).  
  
 You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures. Two overloads cannot differ only in that one has a return value and the other does not.  
  
 You can overload a property the same way you overload a procedure, and with the same restrictions. However, you cannot overload a procedure with a property, or vice versa.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternatives to Overloaded Versions  
 You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.  
  
 Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic. If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.  
  
### <a name="overloads-and-optional-arguments"></a>Overloads and Optional Arguments  
 When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.  
  
#### <a name="when-to-use-overloaded-versions"></a>When to Use Overloaded Versions  
 You can consider defining a series of overloaded versions in the following cases:  
  
- The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.  
  
- The procedure code cannot reliably test whether the calling code has supplied an optional argument. This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.  
  
#### <a name="when-to-use-optional-parameters"></a>When to Use Optional Parameters  
 You might prefer one or more optional parameters in the following cases:  
  
- The only required action when the calling code does not supply an optional argument is to set the parameter to a default value. In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.  
  
 For more information, see [Optional Parameters](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Overloads and ParamArrays  
 When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.  
  
#### <a name="when-to-use-overloaded-versions"></a>When to Use Overloaded Versions  
 You can consider defining a series of overloaded versions in the following cases:  
  
- You know that the calling code never passes more than a small number of values to the parameter array.  
  
- The logic in the procedure code is significantly different depending on how many values the calling code passes.  
  
- The calling code can pass values of different data types.  
  
#### <a name="when-to-use-a-parameter-array"></a>When to Use a Parameter Array  
 You are better served by a `ParamArray` parameter in the following cases:  
  
- You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.  
  
- The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.  
  
 For more information, see [Parameter Arrays](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Implicit Overloads for Optional Parameters  
 A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it. You cannot overload such a procedure with a parameter list corresponding to either of these. The following declarations illustrate this.  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Implicit Overloads for a ParamArray Parameter  
 The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:  
  
- One overload for when the calling code does not supply an argument to the `ParamArray`  
  
- One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type  
  
- For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type  
  
 The following declarations illustrate these implicit overloads.  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array. However, you can use the signatures of the other implicit overloads. The following declarations illustrate this.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Typeless Programming as an Alternative to Overloading  
 If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming. You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option. Then you do not have to declare the parameter's data type. However, this approach has the following disadvantages compared to overloading:  
  
- Typeless programming produces less efficient execution code.  
  
- The procedure must test for every data type it anticipates being passed.  
  
- The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [方法 : プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)
- [方法 : オーバーロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)
- [方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [オーバーロードの解決](./overload-resolution.md)
- [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)
