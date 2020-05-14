---
title: コンストラクター '<name>' はそれ自体を呼び出すことはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 8459ee7fec6d761161a721c88ccdc88e513fc95f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936696"
---
# <a name="constructor-name-cannot-call-itself"></a>コンストラクター '\<name>' はそれ自体を呼び出すことはできません
クラスまたは構造体の `Sub New` プロシージャはそれ自体を呼び出します。  
  
 コンストラクターの目的は、クラスまたは構造体が最初に作成されたときにそのインスタンスを初期化することです。 クラスまたは構造体には、すべてに異なるパラメーター リストが含まれていれば、複数のコンストラクターを含めることができます。 コンストラクターは、別のコンストラクターを呼び出して、独自の機能だけでなくその機能も実行することができます。 ただし、コンストラクターがそれ自体を呼び出す場合は意味がありません。許可されている場合、実際にはこれは無限再帰になります。  
  
 **エラー ID:** BC30298  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 呼び出されるコンストラクターのパラメーター リストを確認します。 これは、呼び出しを行うコンストラクターのものと異なる必要があります。  
  
2. 別のコンストラクターを呼び出さない場合は、`Sub New` 呼び出しを完全に削除します。  
  
## <a name="see-also"></a>関連項目

- [オブジェクトの有効期間:オブジェクトの作成と破棄](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
