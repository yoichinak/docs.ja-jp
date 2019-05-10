---
title: '方法: 変数 (Visual Basic) との間のデータを移動します。'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 033d1cb0116b78ca9e3677c920ee5745117573d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663514"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>方法: 変数 (Visual Basic) との間のデータを移動します。
変数にデータを格納するには、代入ステートメントの左側にある変数名を置きます。  
  
## <a name="putting-data-in-a-variable"></a>変数にデータを配置します。  
  
#### <a name="to-store-a-value-in-a-variable"></a>変数に値を格納するには  
  
- 代入ステートメントの左側にある変数名を使用します。  
  
     次の例では、変数の値を設定する`alpha`します。  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     代入ステートメントの右側にある生成された値は、変数に格納されます。  
  
## <a name="getting-data-from-a-variable"></a>変数からのデータの取得  
 変数の値を取得するには、式の中で変数名を含めます。  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>変数から値を取得するには  
  
- 式の中で変数名を使用します。 変数を使用する任意の場所またはを使用できます、定数、リテラル、以外の定数の値を定義する式の中でします。  
  
     - または -  
  
- 等号の後、変数名を使用して (`=`)、代入ステートメントにサインインします。  
  
     次の例は、変数の値を読み取ります`startValue`し、変数の値を使用して`counter`式で。  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     変数の値は、定数とし、変数または代入ステートメントの左側にあるプロパティに格納されます、式に参加します。  
  
## <a name="see-also"></a>関連項目

- [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
