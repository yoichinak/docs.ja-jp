---
title: '方法: 作成、コレクション初期化子 (Visual Basic) によって使用される拡張メソッドを追加'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: a5af41e25b8f82aa173e2df28cc41b313c8d68dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825405"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>方法: 作成、コレクション初期化子 (Visual Basic) によって使用される拡張メソッドを追加
コレクション初期化子を使用してコレクションを作成するときに、Visual Basic コンパイラ検索、`Add`対象のコレクション型のメソッドのパラメーター、`Add`メソッド コレクション初期化子の値の型に一致します。 これは、`Add`メソッドを使用して、コレクション、コレクション初期化子の値に設定します。  
  
 一致する場合`Add`メソッドが存在して、コレクションのコードを変更することはできません、という拡張メソッドを追加する`Add`コレクション初期化子に必要なパラメータを受け取る。 ジェネリック コレクションに対するコレクション初期化子を使用している場合に行う必要がありますこれは通常です。  
  
## <a name="example"></a>例  
 次の例は、ジェネリック拡張メソッドを追加する方法を示します<xref:System.Collections.Generic.List%601>コレクション初期化子を使用して、型のオブジェクトを追加することになるよう入力`Employee`します。 拡張メソッドでは、簡略化されたコレクションの初期化子構文を使用することができます。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [コレクション初期化子](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [方法: コレクション初期化子を使用してコレクションを作成します。](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
