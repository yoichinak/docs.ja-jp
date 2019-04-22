---
title: '方法: オブジェクト (Visual Basic) の現在のインスタンスを参照してください。'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 3c44748798d5ed554fc9fbded9c3a4d981a66d2f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823364"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>方法: オブジェクト (Visual Basic) の現在のインスタンスを参照してください。
*現在インスタンス*オブジェクトが現在のコードが実行されているインスタンス。  
  
 使用する、`Me`キーワードを現在のインスタンスを参照してください。  
  
### <a name="to-refer-to-the-current-instance"></a>現在のインスタンスを参照するには  
  
-   使用して、`Me`オブジェクト変数の名前を通常使用するキーワード。  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     ただし`Me`オブジェクトと同様に動作変数、宣言またはできないものを割り当てます。 `Me` 常に現在のインスタンスを指します。  
  
## <a name="see-also"></a>関連項目

- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
