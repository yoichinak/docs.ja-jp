---
title: 共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: d6067c75835ecd14f1dd796c20ae3f29f456e541
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642943"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。
宣言された変数、`Shared`修飾子は、共有変数。 共有変数は、1 つだけの記憶域の場所を識別します。 宣言された変数、`WithEvents`修飾子は、変数が属する型が変数で発生させるイベントのセットを処理することをアサートします。 プロパティがによって作成された変数に値が割り当てられると、`WithEvents`宣言は、既存のイベント ハンドラーでアンフックし、を使用して、新しいイベント ハンドラーをフック、`Add`メソッド。  
  
 **エラー ID:** BC30594  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- イベント ハンドラーを宣言`Shared`します。  
  
## <a name="see-also"></a>関連項目

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
