---
title: '方法: オブジェクト変数を宣言し、Visual Basic でオブジェクトを割り当てる'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: fb6411efc190dce335422369a8d2bbff564b9523
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819672"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>方法: オブジェクト変数を宣言し、Visual Basic でオブジェクトを割り当てる
変数を宣言する、 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)を指定して`As Object`で、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)します。 等号の後、オブジェクトを配置することで、このような変数にオブジェクトを代入する (`=`) 代入ステートメントまたは初期化句でします。  
  
## <a name="example"></a>例  
 次の例で、`Object`変数と、現在のインスタンスを割り当てます。  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 宣言の一部として変数を初期化することにより、宣言と代入を組み合わせることができます。 次の例では、前の例と同じです。  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   <xref:System> 名前空間への参照  
  
-   クラス、構造体、または配置されるモジュール、`Dim`ステートメント。  
  
-   代入ステートメントを記述するためのプロシージャです。  
  
## <a name="see-also"></a>関連項目

- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
