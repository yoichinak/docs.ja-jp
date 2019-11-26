---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350748"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Specifies that one or more declared member variables refer to an instance of a class that can raise events.

## <a name="remarks"></a>Remarks

When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.

You can use `WithEvents` only at class or module level. This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.

You cannot use `WithEvents` on a structure member.

You can declare only individual variables—not arrays—with `WithEvents`.

## <a name="rules"></a>ルール

**Element Types.** You must declare `WithEvents` variables to be object variables so that they can accept class instances. However, you cannot declare them as `Object`. You must declare them as the specific class that can raise the events.

The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)

## <a name="example"></a>例

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>関連項目

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
