---
title: "'<interfacename>.<membername>' は、基本クラス '<baseclassname>' によって既に実装されています。 <type> の再実装と見なされます。"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 64bd7771820c2a4073350b7a5189d3a32c4775be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832365"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>'\<interfacename>.\<membername>' は、基本クラス '\<baseclassname>' によって既に実装されています。 \<type> の再実装と見なされます。
プロパティ、プロシージャ、または派生クラスでイベントを使用して、`Implements`句は既に基本クラスで実装されているインターフェイス メンバーを指定します。  
  
 派生クラスでは、その基底クラスによって実装されているインターフェイス メンバーを再実装できます。 このことは、基底クラスの実装をオーバーライドすることとは異なります。 詳細については、「 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)」を参照してください。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。  
  
 **エラー ID:** BC42015  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   インターフェイス メンバーを再実装する場合は、操作を行う必要はありません。 派生クラスのコードで使用しない限り、再実装されたメンバーにアクセスする、`MyBase`キーワードを基底クラスの実装にアクセスします。  
  
-   インターフェイス メンバーを再実装しない場合は、プロパティ、プロシージャ、またはイベント宣言から、 `Implements` 句を削除します。  
  
## <a name="see-also"></a>関連項目

- [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
