---
title: 正しいシグネチャを持つ、アクセス可能な 'Main' メソッドは、'<name>' に見つかりませんでした。
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 559c905d1e2e2de4500771a93d6116f9630011ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591977"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>適切なシグネチャを持つアクセス可能な 'Main' メソッドが見つかりませんでした '\<名 >'
コマンド ライン アプリケーションが必要、`Sub Main`定義します。 `Main` として宣言する必要があります`Public Shared`クラス、またはとして定義されている場合`Public`モジュールで定義されている場合。  
  
 **エラー ID:** BC30737  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 定義、`Public Sub Main`プロジェクト用のプロシージャです。 として宣言`Shared`クラス内で定義する場合にのみです。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic プログラムの構造](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/index.md)
