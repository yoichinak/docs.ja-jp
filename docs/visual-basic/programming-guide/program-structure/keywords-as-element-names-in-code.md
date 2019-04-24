---
title: コード内の要素名としてのキーワード (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: c247ada67f6554362f287cf252dd49856c4995da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841148"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>コード内の要素名としてのキーワード (Visual Basic)
すべてのプログラム要素-変数、クラス、またはメンバーなど、予約されたキーワードと同じ名前を持つことができます。 たとえば、という名前の変数を作成することができます`Loop`します。 ただし、そのバージョンを参照する —、制限されたのと同じ名前を持つ`Loop`キーワード-先頭の完全修飾文字列か、角かっこで囲む必要があります (`[ ]`) 次の例に示すように。  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 これらのうち、どちらも行わないかどうかは、Visual Basic、組み込みの使用を前提としています`Loop`キーワードと、次の例のように、エラーが発生します。  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 角かっこを使用するには、フォームとコントロールを参照するとき、および変数を宣言するか、予約キーワードと同じ名前のプロシージャを定義します。 名を修飾するまたは、角かっこを含めるとため、コードにエラーが発生し、読みにくくなるし忘れることができます。 このため、プログラム要素の名前として予約キーワードを使用しないことをお勧めします。 ただし、将来のバージョンの Visual Basic では、既存のフォームまたはコントロールの名前と競合する新しいキーワードを定義する場合しすることができますを使用して、この手法、コードを更新するときに、新しいバージョンを使用します。  
  
> [!NOTE]
>  プログラムは、他の参照先アセンブリによって提供される要素名もなどがあります。 これらの名前が制限されているキーワードと競合する場合は、Visual Basic は定義された要素として解釈すると、周囲に角かっこでいます。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
