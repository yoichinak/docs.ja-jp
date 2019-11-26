---
title: パラメーターと引数の違い
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: c4249dbf86bd1bfa7ef08e94059d2880333e9a92
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341375"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>パラメーターと引数の違い (Visual Basic)
In most cases, a procedure must have some information about the circumstances in which it has been called. A procedure that performs repeated or shared tasks uses different information for each call. This information consists of variables, constants, and expressions that you pass to the procedure when you call it.  
  
 To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter. You can think of the parameter as a parking space and the argument as an automobile. Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.  
  
## <a name="parameters"></a>パラメーター  
 A *parameter* represents a value that the procedure expects you to pass when you call it. The procedure's declaration defines its parameters.  
  
 When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name. For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). You can also indicate that a parameter is optional. This means that the calling code does not have to pass a value for it.  
  
 The name of each parameter serves as a *local variable* in the procedure. You use the parameter name the same way you use any other variable.  
  
## <a name="arguments"></a>引数  
 An *argument* represents the value that you pass to a procedure parameter when you call the procedure. The calling code supplies the arguments when it calls the procedure.  
  
 When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name. Each argument corresponds to the parameter in the same position in the list.  
  
 In contrast to parameter definition, arguments do not have names. Each argument is an expression, which can contain zero or more variables, constants, and literals. The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [方法 : プロシージャにパラメーターを定義する](./how-to-define-a-parameter-for-a-procedure.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [再帰プロシージャ](./recursive-procedures.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
