---
title: '方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 047d566c13f03803d2e5c3bc6cce0db56df4a3f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345851"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)
If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array. For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>To overload a procedure that takes a variable number of parameters  
  
1. Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter. See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).  
  
2. Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list. This might include the case of no value, and it might include the case of a single one-dimensional array.  
  
3. For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list. Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.  
  
4. In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.  
  
5. Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.  
  
6. Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.  
  
## <a name="example"></a>例  
 The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array. However, you can use the signatures of the other implicit overloads. The following declarations illustrate this.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many. Visual Basic passes control to the version matching the calling argument list.  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads. For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application. If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [省略可能なパラメーター](./optional-parameters.md)
- [パラメーター配列](./parameter-arrays.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [方法 : プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)
- [方法 : オーバーロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)
- [方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [オーバーロードの解決](./overload-resolution.md)
