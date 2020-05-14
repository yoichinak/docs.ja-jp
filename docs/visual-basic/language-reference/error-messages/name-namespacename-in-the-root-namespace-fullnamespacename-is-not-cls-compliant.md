---
title: ルート名前空間 <namespacename> にある名前 <fullnamespacename> は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 821044d3ee359a052fa6a763e9c5a89da5d6f607
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775582"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>ルート名前空間 \<fullnamespacename> にある名前 \<namespacename> は CLS に準拠していません
アセンブリが `<CLSCompliant(True)>` としてマークされているのに、ルート名前空間の名前の要素がアンダースコア (`_`) で始まっています。  
  
 プログラミング要素には 1 つ以上のアンダースコアを含めることができますが、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠するためには、先頭をアンダースコアにしてはなりません。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。  
  
 **エラー ID:** BC40039  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- CLS 準拠にする必要がある場合は、ルート名前空間の名前を変更し、その要素がアンダースコアで始まらないようにします。  
  
- 名前空間の名前が変更されないようにする必要がある場合は、アセンブリから <xref:System.CLSCompliantAttribute> を削除するか、アセンブリを `<CLSCompliant(False)>` としてマークします。  
  
## <a name="see-also"></a>関連項目

- [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
