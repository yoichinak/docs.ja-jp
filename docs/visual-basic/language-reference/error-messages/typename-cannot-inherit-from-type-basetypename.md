---
title: ベース <typename> のアクセスをアセンブリの外側に展開しているため、'<type>' は <basetypename> '<type>' から継承できません。
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764362"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<typename >' から継承できません\<型 >'\<basetypename >' ベースのアクセスを展開するので、\<型 >、アセンブリ外
クラスまたはインターフェイスは、基本クラスから継承されているかインターフェイスより制限の少ないアクセス レベル。  
  
 たとえば、`Public`インターフェイスから継承、`Friend`インターフェイス、または`Protected`クラスから継承、`Private`クラス。 これは、基底クラスまたはインターフェイスの目的のレベルを超えてへのアクセスに公開します。  
  
 **エラー ID:** BC30910  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 派生クラスまたは少なくとも基底クラスまたはインターフェイスの場合と同程度に制限するようにインターフェイスのアクセス レベルを変更します。  
  
     - または -  
  
- 制限の少ないアクセス レベルが必要な場合は、削除、`Inherits`ステートメント。 さらに制限された基底クラスまたはインターフェイスから継承することはできません。  
  
## <a name="see-also"></a>関連項目

- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
