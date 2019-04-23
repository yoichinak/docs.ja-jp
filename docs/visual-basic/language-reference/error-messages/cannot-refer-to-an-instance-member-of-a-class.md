---
title: クラスの明示的なインスタンスを指定しないで、共有メソッドまたは共有メンバー初期化子内からクラスのインスタンス メンバーへ参照することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: aad068b5857eb956ded63fa2a57cb163d3cf5c58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322694"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>クラスの明示的なインスタンスを指定しないで、共有メソッドまたは共有メンバー初期化子内からクラスのインスタンス メンバーへ参照することはできません。
共有プロシージャ内からクラスの非共有メンバーを参照しようとしました。 次の例では、このような状況を示します。  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 前の例では、代入ステートメント`x = 10`このエラー メッセージが生成されます。 これは、ため、インスタンス変数にアクセスしようとして共有プロシージャです。  
  
 変数`x`として宣言されていないため、インスタンス メンバーは、 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)します。 クラスの各インスタンス`sample`独自の個別の変数が含まれる`x`します。 1 つのインスタンスを設定またはの値を変更すると`x`の値には影響しません`x`他のインスタンス。  
  
 ただし、プロシージャ`setX`は`Shared`クラスのすべてのインスタンス間で`sample`します。 これではなく個々 のインスタンスとは独立して動作しますが、クラスのインスタンスのいずれかに関連付けられていないことを意味します。 特定のインスタンスとの接続があるないため`setX`インスタンス変数にアクセスすることはできません。 のみ動作する必要があります、`Shared`変数。 ときに`setX`その新しい値が、クラスのすべてのインスタンスで使用できる、共有変数の値を変更または設定します。  
  
 **エラー ID:** BC30369  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. クラスのすべてのインスタンス間で共有またはインスタンスごとに保持するメンバーにするかどうかを決定します。  
  
2. すべてのインスタンス間で共有するメンバーの 1 つのコピーを実行する場合に、追加、`Shared`メンバーの宣言にキーワード。 保持、`Shared`プロシージャ宣言でキーワード。  
  
3. 各インスタンスでメンバーの独自の個別コピーが存在する場合を指定しない`Shared`メンバーの宣言にします。 削除、`Shared`プロシージャ宣言からキーワード。  
  
## <a name="see-also"></a>関連項目

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
