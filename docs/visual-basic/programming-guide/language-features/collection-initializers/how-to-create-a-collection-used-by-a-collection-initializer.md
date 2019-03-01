---
title: '方法: コレクション初期化子 (Visual Basic) を使用してコレクションを作成します。'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: d0007ebf5f18dee5bd8448a071fe1f0f984aff1a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967452"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>方法: コレクション初期化子 (Visual Basic) を使用してコレクションを作成します。
コレクション初期化子を使用してコレクションを作成するときに、Visual Basic コンパイラ検索、`Add`対象のコレクション型のメソッドのパラメーター、`Add`メソッド コレクション初期化子の値の型に一致します。 これは、`Add`メソッドを使用して、コレクション、コレクション初期化子の値に設定します。  
  
## <a name="example"></a>例  
 次の例は、`OrderCollection`パブリックを含むコレクション`Add`コレクション初期化子を使用して型のオブジェクトの追加メソッド`Order`します。 `Add`メソッドでは、簡略化されたコレクションの初期化子構文を使用することができます。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目
- [コレクション初期化子](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [方法: 作成、コレクション初期化子によって使用される拡張メソッドを追加](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
