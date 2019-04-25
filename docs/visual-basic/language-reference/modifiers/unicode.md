---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b3c9452f8d144fb18ea3efcb35b85caed80e8692
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819347"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Visual Basic に宣言されている外部プロシージャの名前に関係なく Unicode 値にすべての文字列がマーシャ リングする必要がありますを指定します。  
  
 プロジェクトの外部で定義されたプロシージャを呼び出すときに、Visual Basic コンパイラには、手順を正しく呼び出すために必要があります情報へのアクセスはありません。 この情報には、プロシージャがある場所は、識別方法、その呼び出し元のシーケンスおよび戻り値の型が含まれます。 して、使用する文字列の文字セットします。 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)外部プロシージャへの参照を作成し、このために必要な情報を提供します。  
  
 `charsetmodifier`パーツ、`Declare`ステートメントが外部プロシージャの呼び出し中に文字列をマーシャ リングする、文字セット情報を提供します。 また、Visual Basic が外部プロシージャ名の外部のファイルを検索する方法も影響します。 `Unicode`修飾子は、Visual Basic を Unicode 値のすべての文字列をマーシャ リングする必要があり、検索中にその名前を変更することがなく、プロシージャを検索することを指定します。  
  
 文字セットに修飾子が指定されていない場合`Ansi`既定値です。  
  
## <a name="remarks"></a>Remarks  
 `Unicode`修飾子は、このコンテキストで使用できます。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>スマート デバイスの開発者向け注意事項  
 このキーワードはサポートされていません。  
  
## <a name="see-also"></a>関連項目

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
