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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662057"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>プロパティのアクセサーを 'get''\<propertyname >' にアクセスできません
ステートメントが、プロパティへのアクセスがあるない場合は、プロパティの値を取得しようとしています。`Get`プロシージャ。  
  
 場合、 [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)レベルよりもより制限の厳しいアクセスでマークされたその[Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)プロパティの値を読み取ろうとしてが失敗する、次の場合。  
  
- `Get`ステートメントがマークされている[プライベート](../../../visual-basic/language-reference/modifiers/private.md)呼び出し元のコードとそれには、クラスまたは構造体のプロパティが定義されているとします。  
  
- `Get`ステートメントがマークされている[Protected](../../../visual-basic/language-reference/modifiers/protected.md)呼び出し元のコードは、クラスまたはプロパティが定義されている構造体ではなく、派生クラスでも。  
  
- `Get`ステートメントがマークされている[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)プロパティが定義されている同じアセンブリに呼び出し元のコードがないとします。  
  
 **エラー ID:** BC31103  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- コントロールのプロパティを定義するソース コードを使っている場合を宣言することを検討してください、`Get`プロパティ自体と同じアクセス レベルを持つプロシージャ。  
  
- 場合は、プロパティを定義するソース コードがないか、または制限する必要があります、`Get`プロパティ自体へのアクセス性のあるコードの領域にプロパティ値を読み取るステートメントに移動しようとする複数のプロシージャ アクセス レベル、プロパティ。  
  
## <a name="see-also"></a>関連項目

- [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [方法: 混合アクセス レベルを持つプロパティを宣言します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
