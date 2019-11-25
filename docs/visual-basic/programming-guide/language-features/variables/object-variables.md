---
title: オブジェクト変数
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7eb860bc732f923316b8ce1d7b94ecdb368bfec3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351792"
---
# <a name="object-variables-in-visual-basic"></a>Visual Basic におけるオブジェクト変数

In addition to storing values directly, a variable can refer to an object. You assign an object to a variable for the same reasons you assign any value to a variable:

- A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.

- Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.

- You can change a variable to refer to other objects while your code is running.

## <a name="making-code-shorter"></a>Making Code Shorter

You can use object variables to shorten the code you have to type. The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

You can shorten this code, and speed up execution, if you use an object variable for the control. You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case). Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers. You can set or retrieve the properties of the object or use any of its methods. The following example uses an object variable to simplify the code in the preceding example.

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>関連項目

- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [方法 : 長い修飾パスを持つオブジェクトへのアクセス時間を短縮する](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
