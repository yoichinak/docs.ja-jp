---
title: '方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 4d31980e4b968cff274091ba4f307dffddab1100
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350864"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)
If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads. For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>One Optional Parameter  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>To overload a procedure that takes one optional parameter  
  
1. Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list. Do not use the `Optional` keyword in this overloaded version.  
  
2. Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.  
  
3. Write the procedure code that should execute when the calling code supplies the optional argument.  
  
4. Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.  
  
5. Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.  
  
6. Write the procedure code that should execute when the calling code does not supply the optional argument. Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.  
  
     The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Multiple Optional Parameters  
 For a procedure with more than one optional parameter, you normally need more than two overloaded versions. For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.  
  
 As the number of optional parameters increases, the complexity of the overloading increases. Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions. Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>To overload a procedure that takes more than one optional parameter  
  
1. Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure. An unacceptable combination might arise if one optional parameter depends on another. For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.  
  
2. For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list. Do not use the `Optional` keyword.  
  
3. In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.  
  
4. Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.  
  
5. Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [省略可能なパラメーター](./optional-parameters.md)
- [パラメーター配列](./parameter-arrays.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [方法 : プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)
- [方法 : オーバーロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)
- [方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [オーバーロードの解決](./overload-resolution.md)
