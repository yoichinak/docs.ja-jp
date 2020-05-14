---
title: Default
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
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351577"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
クラス、構造体、またはインターフェイスの既定のプロパティとしてプロパティを識別します。  
  
## <a name="remarks"></a>Remarks  
 プロパティが少なくとも 1 つのパラメーターを受け取る場合、クラス、構造体、またはインターフェイスは、そのプロパティの 1 つだけを*既定のプロパティ*として指定できます。 コードがメンバーを指定せずにクラスまたは構造体を参照する場合、Visual Basic はその参照を既定のプロパティに解決します。  
  
 既定のプロパティを使用すると、ソース コード文字が少し少なくなる可能性がありますが、コードが読みにくくなる可能性があります。 呼び出し元のコードがクラスまたは構造体をよく理解していない場合は、クラスまたは構造体の名前を参照するときに、その参照がクラスまたは構造体自体、または既定のプロパティにアクセスするかどうかがわかりません。 これにより、コンパイラ エラーや実行時の微妙なロジック エラーが発生する可能性があります。  
  
 常に [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)を使用してコンパイラの型チェックを `On` に設定することにより、既定のプロパティ エラーが発生する可能性を多少減らすことができます。  
  
 定義済みのクラスまたは構造体をコード内で使用する予定の場合は、既定のプロパティがあるかどうかと、ある場合はその名前を確認する必要があります。  
  
 これらの欠点があるため、既定のプロパティを定義しないことを検討してください。 コードを読みやすくするためには、既定のプロパティを含め、常にすべてのプロパティを明示的に参照することも検討してください。  
  
 `Default` 修飾子は、次のコンテキストで使用できます。  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目

- [方法: 既定のプロパティを宣言して呼び出す (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
