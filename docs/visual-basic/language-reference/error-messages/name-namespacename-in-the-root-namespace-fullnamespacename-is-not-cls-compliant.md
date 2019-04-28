---
title: ルート名前空間 <namespacename> にある名前 <fullnamespacename> は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 84706719d151ea8df478f88610df34842f6f8702
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918360"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>名前\<namespacename > ルート名前空間で\<fullnamespacename > CLS 準拠ではありません
アセンブリをマーク`<CLSCompliant(True)>`、ルート名前空間の名前の要素は、アンダー スコアで始まるが、(`_`)。  
  
 プログラミング要素ですが準拠するため、1 つまたは複数アンダー スコアを含めることができます、 [Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS) にする必要がありますされませんアンダー スコアで始まりです。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、準拠または非準拠を示すために、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。  
  
 **エラー ID:** BC40039  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- CLS 準拠が必要な場合は、ルート名前空間の名前を変更してから、アンダー スコアで始まる要素がないようにします。  
  
- 削除し、名前空間の名前を変更できないことが必要な場合、<xref:System.CLSCompliantAttribute>アセンブリからとしてマークまたは`<CLSCompliant(False)>`します。  
  
## <a name="see-also"></a>関連項目

- [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
