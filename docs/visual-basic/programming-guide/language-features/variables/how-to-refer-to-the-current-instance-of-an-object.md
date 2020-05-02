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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346882"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>方法: オブジェクトの現在のインスタンスを参照する (Visual Basic)
オブジェクトの "*現在のインスタンス*" は、コードが現在実行されているインスタンスです。  
  
 現在のインスタンスを参照するには、`Me` キーワードを使用します。  
  
### <a name="to-refer-to-the-current-instance"></a>現在のインスタンスを参照するには  
  
- オブジェクト変数の名前を通常使用する箇所で `Me` キーワードを使用します。  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     `Me` はオブジェクト変数と同様に動作しますが、宣言したり、何かを代入したりすることはできません。 `Me` では常に現在のインスタンスが参照されます。  
  
## <a name="see-also"></a>関連項目

- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
