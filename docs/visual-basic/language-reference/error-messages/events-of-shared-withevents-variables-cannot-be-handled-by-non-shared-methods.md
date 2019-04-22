---
title: 共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838652"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。
宣言された変数、`Shared`修飾子は、共有変数。 共有変数は、1 つだけの記憶域の場所を識別します。 宣言された変数、`WithEvents`修飾子は、変数が属する型が変数で発生させるイベントのセットを処理することをアサートします。 プロパティがによって作成された変数に値が割り当てられると、`WithEvents`宣言は、既存のイベント ハンドラーでアンフックし、を使用して、新しいイベント ハンドラーをフック、`Add`メソッド。  
  
 **エラー ID:** BC30594  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   イベント ハンドラーを宣言`Shared`します。  
  
## <a name="see-also"></a>関連項目

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
