---
title: Error ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351245"
---
# <a name="error-statement"></a>Error ステートメント
Simulates the occurrence of an error.  
  
## <a name="syntax"></a>構文  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>指定項目  
 `errornumber`  
 必須です。 Can be any valid error number.  
  
## <a name="remarks"></a>Remarks  
 The `Error` statement is supported for backward compatibility. In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.  
  
 If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:  
  
|property|[値]|  
|--------------|-----------|  
|`Number`|Value specified as argument to `Error` statement. Can be any valid error number.|  
|`Source`|Name of the current Visual Basic project.|  
|`Description`|String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists. If the string does not exist, `Description` contains a zero-length string ("").|  
|`HelpFile`|The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.|  
|`HelpContext`|The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.|  
|`LastDLLError`|Zero.|  
  
 If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.  
  
> [!NOTE]
> Some Visual Basic host applications cannot create objects. See your host application's documentation to determine whether it can create classes and objects.  
  
## <a name="example"></a>例  
 This example uses the `Error` statement to generate error number 11.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>［要件］  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume ステートメント](../../../visual-basic/language-reference/statements/resume-statement.md)
- [エラー メッセージ](../../../visual-basic/language-reference/error-messages/index.md)
