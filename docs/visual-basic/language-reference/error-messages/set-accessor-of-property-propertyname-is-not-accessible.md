---
title: プロパティ '<propertyname>' の 'Set' アクセサーにアクセスできません。
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3bc50d6762998ca5d8f445d84c8b698c9f46436f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055148"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a>'Set' アクセサー プロパティの '\<propertyname >' にアクセスできません
ステートメントが、プロパティへのアクセスがあるないときに、プロパティの値を格納しようとしています。`Set`プロシージャ。  
  
 場合、 [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)レベルよりもより制限の厳しいアクセスでマークされたその[Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)プロパティ値を設定しようとするが失敗する、次の場合。  
  
- `Set`ステートメントがマークされている[プライベート](../../../visual-basic/language-reference/modifiers/private.md)呼び出し元のコードとそれには、クラスまたは構造体のプロパティが定義されているとします。  
  
- `Set`ステートメントがマークされている[Protected](../../../visual-basic/language-reference/modifiers/protected.md)呼び出し元のコードは、クラスまたはプロパティが定義されている構造体ではなく、派生クラスでも。  
  
- `Set`ステートメントがマークされている[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)プロパティが定義されている同じアセンブリに呼び出し元のコードがないとします。  
  
 **エラー ID:** BC31102  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- コントロールのプロパティを定義するソース コードを使っている場合を宣言することを検討してください、`Set`プロパティ自体と同じアクセス レベルを持つプロシージャ。  
  
- 場合は、プロパティを定義するソース コードがないか、または制限する必要があります、`Set`プロパティ自体にアクセスするより優れたコードの領域にプロパティ値を設定するステートメントに移動しようとする複数のプロシージャ アクセス レベル、プロパティ。  
  
## <a name="see-also"></a>関連項目

- [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [方法: 混合アクセス レベルを持つプロパティを宣言します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
