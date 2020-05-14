---
title: ベース <typename> のアクセスをアセンブリの外側に展開しているため、'<type>' は <basetypename> '<type>' から継承できません。
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: e21eea20d953e64e91522074c25f037451145bf8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664209"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<typename>' は、基底 \<type> のアクセスをアセンブリの外側に展開しているため、\<type> '\<basetypename>' から継承できません
クラスまたはインターフェイスは、基底クラスまたはインターフェイスから継承されますが、アクセス レベルの制限が緩くなります。  
  
 たとえば、`Public` インターフェイスは `Friend` インターフェイスから継承し、または `Protected` クラスは、`Private` クラスから継承します。 これにより、目的のレベルを超えてアクセスする基底クラスまたはインターフェイスが公開されます。  
  
 **エラー ID:** BC30910  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 派生クラスまたはインターフェイスのアクセス レベルを、少なくとも基底クラスまたはインターフェイスのアクセス レベルの制限になるように変更します。  
  
     \- または -  
  
- 制限の緩いアクセス レベルが必要な場合は、`Inherits` ステートメントを削除します。 より制限の厳しい基底クラスまたはインターフェイスから継承することはできません。  
  
## <a name="see-also"></a>関連項目

- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
