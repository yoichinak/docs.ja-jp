---
title: クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 14c498bf3067415f8de2afaeaaa57cf3f28ae857
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58045272"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。
クラスの既定のインスタンスは、クラス コンストラクターで使用されています。 これは、無限ループとも呼ばれる、無限の再帰呼び出しを引き起こす可能性があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   クラス コンストラクターから、既定のインスタンスを削除します。  
  
## <a name="see-also"></a>関連項目

- [コンストラクター](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
