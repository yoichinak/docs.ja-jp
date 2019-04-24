---
title: 正しいシグネチャを持つ、アクセス可能な 'Main' メソッドは、'<name>' に見つかりませんでした。
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: f5053bddf4b9ba791ad6d0733e1dd89c4ded91bd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818359"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>適切なシグネチャを持つアクセス可能な 'Main' メソッドが見つかりませんでした '\<名 >'
コマンド ライン アプリケーションが必要、`Sub Main`定義します。 `Main` として宣言する必要があります`Public Shared`クラス、またはとして定義されている場合`Public`モジュールで定義されている場合。  
  
 **エラー ID:** BC30737  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   定義、`Public Sub Main`プロジェクト用のプロシージャです。 として宣言`Shared`クラス内で定義する場合にのみです。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic プログラムの構造](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/index.md)
