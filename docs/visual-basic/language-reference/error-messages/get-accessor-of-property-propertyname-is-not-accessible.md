---
title: プロパティ '<propertyname>' の 'Get' アクセサーにアクセスできません。
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 92cc6d732b59617a6043bd71a9549649ff1ad356
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662057"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>プロパティ '\<propertyname>' の 'Get' アクセサーにアクセスできません
ステートメントは、プロパティの `Get` プロシージャにアクセスできない場合に、プロパティの値を取得しようとします。  
  
 [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)がその [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)よりも制限の厳しいアクセス レベルでマークされている場合は、プロパティ値を読み取ろうとすると、次のような場合は失敗する可能性があります。  
  
- `Get` ステートメントが [Private](../../../visual-basic/language-reference/modifiers/private.md) とマークされていて、呼び出し元のコードが、プロパティが定義されているクラスまたは構造体の外側にある。  
  
- `Get` ステートメントが [Protected](../../../visual-basic/language-reference/modifiers/protected.md) とマークされていて、呼び出し元のコードが、プロパティが定義されているクラスまたは構造体内にも、派生クラス内にもない。  
  
- `Get` ステートメントが [Friend](../../../visual-basic/language-reference/modifiers/friend.md) とマークされていて、呼び出し元のコードが、プロパティが定義されているアセンブリと同じアセンブリ内にない。  
  
 **エラー ID:** BC31103  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- プロパティを定義するソース コードを制御できる場合は、プロパティ自体と同じアクセス レベルで `Get` プロシージャを宣言することを検討してください。  
  
- プロパティを定義するソース コードを制御できない場合、またはプロパティ自体よりも `Get` プロシージャのアクセス レベルを制限する必要がある場合は、プロパティ値を読み取るステートメントを、プロパティによりアクセスしやすいコードの領域に移動してみてください。  
  
## <a name="see-also"></a>関連項目

- [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [方法: 複数のアクセス レベルを持つプロパティを宣言する](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
