---
title: クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 1cad1e3cf3943e945d519aee061a877c91684b4a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623469"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。
クラスの既定のインスタンスは、クラス コンストラクターで使用されています。 これは、無限ループとも呼ばれる、無限の再帰呼び出しを引き起こす可能性があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- クラス コンストラクターから、既定のインスタンスを削除します。  
  
## <a name="see-also"></a>関連項目

- [コンストラクター](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
