---
title: メソッド '<methodname>' には、同じシグネチャを持つ複数の定義が含まれています。
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: fe8d1d8e11e25bcd79894ed82a57dd06748c3d68
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831879"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a>'\<methodname >' が同じシグネチャを持つ複数の定義
`Function`または`Sub`プロシージャ宣言では、前の宣言と同じプロシージャの名前と引数のリストを使用します。 1 つの考えられる原因は、元のプロシージャをオーバー ロードする試みです。 オーバー ロードされたプロシージャには、異なる引数リストが必要です。  
  
 **エラー ID:** BC30269  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   プロシージャ名か、引数リストを変更するか、重複の宣言を削除します。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [プロシージャのオーバーロードに関する注意事項](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
