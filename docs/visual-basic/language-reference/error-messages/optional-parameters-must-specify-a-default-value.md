---
title: 省略可能な引数には、既定値を指定する必要があります。
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 01c0abb366e8605a9b153333e645fc3276b6bd16
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821726"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>省略可能な引数には、既定値を指定する必要があります。
省略可能なパラメーターは、呼び出し元のプロシージャでパラメーターが指定されていない場合に使用できる既定値を指定する必要があります。  
  
 **エラー ID:** BC30812  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   は省略可能なパラメーターの既定値を指定します例えば：  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a>関連項目

- [Optional](../../../visual-basic/language-reference/modifiers/optional.md)
