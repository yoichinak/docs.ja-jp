---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 75d118ee2bd4918c3a936cb341864ddc5315726b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826614"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
1 つまたは複数の宣言されたメンバー変数がイベントを発生させるクラスのインスタンスを参照しているを指定します。  
  
## <a name="remarks"></a>Remarks  
 使用して変数を定義するとき`WithEvents`、メソッドを使用して、変数のイベントを処理することを宣言によって指定できます、`Handles`キーワード。  
  
 使用することができます`WithEvents`クラスまたはモジュール レベルでのみです。 これは、意味の宣言コンテキスト、`WithEvents`変数がクラスまたはモジュールにある必要があるあり、ソース ファイル、名前空間、構造体、またはプロシージャにすることはできません。  
  
 使用することはできません`WithEvents`構造体のメンバーにします。  
  
 個々 の変数を宣言することができます: 配列ではありません — で`WithEvents`します。  
  
## <a name="rules"></a>ルール  
  
-   **要素の型。** 宣言する必要があります`WithEvents`の変数を受け付けることができるため、オブジェクト変数クラスのインスタンス。 ただし、としてを宣言できません`Object`します。 イベントを発生させる特定のクラスとして宣言する必要があります。  
  
 `WithEvents`修飾子は、このコンテキストで使用できます。[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
