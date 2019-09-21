---
title: コード内の要素名としてのキーワード (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 2e3613bd4a74da51cf7dbb63e52eddca811ca8e1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947662"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>コード内の要素名としてのキーワード (Visual Basic)
すべてのプログラム要素 (変数、クラス、メンバーなど) は、制限付きキーワードと同じ名前を持つことができます。 たとえば、という名前`Loop`の変数を作成できます。 ただし、制限付き`Loop`キーワードと同じ名前を持つバージョンを参照するには、次の例に示すように、完全修飾文字列を使用するか、角かっこ (`[ ]`) で囲む必要があります。  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 これらのいずれも実行しない場合、Visual Basic は、次の例に`Loop`示すように、組み込みキーワードを使用することを前提とし、エラーを生成します。  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 フォームとコントロールを参照する場合や、変数を宣言する場合、または制限されたキーワードと同じ名前のプロシージャを定義する場合は、角かっこを使用できます。 名前を修飾したり、角かっこを含めたりすることは簡単ではありません。したがって、コードにエラーが発生して読みにくくなります。 このため、プログラム要素の名前として制限付きキーワードを使用しないことをお勧めします。 ただし、Visual Basic の将来のバージョンで、既存のフォーム名またはコントロール名と競合する新しいキーワードが定義されている場合は、新しいバージョンで動作するようにコードを更新するときに、この手法を使用できます。  
  
> [!NOTE]
> プログラムには、他の参照アセンブリによって提供される要素名を含めることもできます。 これらの名前が制限付きキーワードと競合している場合は、角かっこを配置すると、Visual Basic によって定義済みの要素として解釈されます。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic 名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
