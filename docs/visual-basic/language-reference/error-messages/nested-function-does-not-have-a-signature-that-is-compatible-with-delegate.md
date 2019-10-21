---
title: 入れ子になった関数に、デリゲート '<delegatename>' と互換性のあるシグネチャがありません。
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: d65c8eab661675c955ff6562098248c04036d6e7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580643"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>入れ子になった関数に、デリゲート ' \<delegatename > ' と互換性のあるシグネチャがありません

互換性のないシグネチャを持つデリゲートにラムダ式が割り当てられています。 たとえば、次のコードでは、delegate `Del` に2つの整数パラメーターがあります。

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

1つの引数を持つラムダ式が `Del` 型として宣言されている場合、エラーが発生します。

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

**エラー ID:** BC36532

## <a name="to-correct-this-error"></a>このエラーを解決するには

デリゲート定義または割り当てられたラムダ式を調整して、シグネチャに互換性を持たせるようにします。

## <a name="see-also"></a>関連項目

- [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
