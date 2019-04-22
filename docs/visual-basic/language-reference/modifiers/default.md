---
title: Default (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: f78ffe42a9d618d44da2a50c0de831396576430c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836728"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
クラス、構造体、またはインターフェイスの既定のプロパティとしてプロパティを識別します。  
  
## <a name="remarks"></a>Remarks  
 クラス、構造体、またはインターフェイスは多くて 1 つとしてのプロパティで指定できます、*プロパティの既定*、そのプロパティは、少なくとも 1 つのパラメーターを受け取ります。 コードでは、クラスまたは構造体への参照をメンバーを指定しなくても、Visual Basic は、既定のプロパティには、その参照を解決します。  
  
 既定のプロパティは、ソース コードの文字のわずかな低下につながるが行えるように、コードが読みにくくします。 クラスまたは構造体名への参照を行うときに、呼び出し元のコードがクラスまたは構造に習熟していない場合にすることはできません特定その参照が、クラスまたは構造体自体、または既定のプロパティにアクセスするかどうか。 これについては、コンパイラ エラーまたはランタイム ロジックの微妙なエラーにつながります。  
  
 常を使用して既定のプロパティのエラーの可能性を低くことができますやや、 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)コンパイラ型チェックを設定する`On`します。  
  
 使用して、定義済みのクラスまたは構造体コードで判断する必要があります、既定のプロパティがあるかどうかであればしようとしている場合、名前は。  
  
 このような短所のためには、既定のプロパティを定義しないを検討してください。 コードを読みやすくは必要がありますも常に明示的に参照するすべてのプロパティを検討してくださいも既定のプロパティ。  
  
 `Default`修飾子は、このコンテキストで使用できます。  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目

- [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
