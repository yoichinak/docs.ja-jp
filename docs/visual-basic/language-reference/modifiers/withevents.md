---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 50d5a768393e90d28d150b451405e35e6f4c7953
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583041"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
1つ以上の宣言されたメンバー変数が、イベントを発生させることができるクラスのインスタンスを参照することを指定します。

## <a name="remarks"></a>Remarks

@No__t_0 を使用して変数が定義されている場合は、メソッドが `Handles` キーワードを使用して変数のイベントを処理するように、宣言によって指定できます。

@No__t_0 は、クラスレベルまたはモジュールレベルでのみ使用できます。 つまり、`WithEvents` 変数の宣言コンテキストは、クラスまたはモジュールである必要があり、ソースファイル、名前空間、構造体、またはプロシージャにすることはできません。

構造体メンバーで `WithEvents` を使用することはできません。

@No__t_0 では、配列ではなく個々の変数のみを宣言できます。

## <a name="rules"></a>ルール

**要素の型。** オブジェクト変数として `WithEvents` 変数を宣言して、クラスのインスタンスを受け入れるようにする必要があります。 ただし、`Object` として宣言することはできません。 これらのクラスは、イベントを発生させることができる特定のクラスとして宣言する必要があります。

@No__t_0 修飾子は、次のコンテキストで使用できます: [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)

## <a name="example"></a>例

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>関連項目

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
