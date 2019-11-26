---
title: '方法: オブジェクトの現在のインスタンスを参照する'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 62b22a54904a45380052d3d81d9415517d4f8d3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346882"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>方法: オブジェクトの現在のインスタンスを参照する (Visual Basic)
The *current instance* of an object is the instance in which the code is currently executing.  
  
 You use the `Me` keyword to refer to the current instance.  
  
### <a name="to-refer-to-the-current-instance"></a>To refer to the current instance  
  
- Use the `Me` keyword where you would normally use the name of an object variable.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Although `Me` behaves like an object variable, you cannot declare it or assign anything to it. `Me` always refers to the current instance.  
  
## <a name="see-also"></a>関連項目

- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
