---
title: 属性 '<attributename>' を複数回適用することはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: da4a766e2617308cb33b9673a88db9e7a954152a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935318"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>属性 '\<attributename >' 複数回適用できません
属性は、1 回のみ適用できます。 `AttributeUsage`属性が属性を複数回適用できるかどうかを決定します。  
  
 **エラー ID:** BC30663  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 属性は 1 回のみ適用することを確認します。  
  
2. 開発したカスタム属性を使用している場合は、変更することを検討してください、`AttributeUsage`の次の例と同じ複数の属性の使用を許可する属性。  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.AttributeUsageAttribute>
- [カスタム属性の作成](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
