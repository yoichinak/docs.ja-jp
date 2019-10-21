---
title: 省略可能な引数には、既定値を指定する必要があります。
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 8ec4627d070cc670ce04be3a5d0298dba0a279d0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582134"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>省略可能な引数には、既定値を指定する必要があります。

省略可能なパラメーターには、呼び出し元のプロシージャによってパラメーターが指定されていない場合に使用できる既定値を指定する必要があります。

**エラー ID:** BC30812

## <a name="to-correct-this-error"></a>このエラーを解決するには

省略可能なパラメーターの既定値を指定します。例えば：

```vb
Sub Proc1(ByVal X As Integer,
      Optional ByVal Y As String = "Default Value")
    MsgBox("Default argument is: " & Y)
End Sub
```

## <a name="see-also"></a>関連項目

- [Optional](../../../visual-basic/language-reference/modifiers/optional.md)
