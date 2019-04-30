---
title: 構造体 '<structurename>' は少なくとも 1 つのインスタンス メンバー変数、または 'Custom' に設定されていない少なくとも 1 つのインスタンス イベント宣言を含まなければなりません。
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 598aef3943a53ee6eb97064819c9128de1839f52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055109"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>構造体 '\<structurename >' に少なくとも 1 つのインスタンス メンバー変数または 'Custom' にマークされていない少なくとも 1 つのインスタンス イベント宣言を含める必要があります
構造体の定義は、すべての非共有変数または非共有の非カスタム イベントには含まれません。  
  
 すべての構造体を変数またはイベントをまとめて、すべてのインスタンスに (共有) の代わりに特定のインスタンスに適用されますが適用される場合があります ([Shared](../../../visual-basic/language-reference/modifiers/shared.md))。 非共有の定数、プロパティ、およびプロシージャは、この要件を満たしていません。 さらに、非共有変数がなく、1 つだけの非共有イベントがある場合は、そのイベントすることはできません、`Custom`イベント。  
  
 **エラー ID:** BC30941  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 少なくとも 1 つの変数またはイベントでない定義`Shared`します。 1 つのみのイベントを定義する場合は、カスタムではないと非共有があります。  
  
## <a name="see-also"></a>関連項目

- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [方法: 構造体を宣言する](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
