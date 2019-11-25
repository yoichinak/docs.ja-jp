---
title: '方法 : コードのセクションを折りたたんで非表示にする'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: e7aacdc3f41199127b00d276b382ec4a5f258da0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347409"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>方法: コードのセクションを折りたたんで非表示にする (Visual Basic)

The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files. The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor. The ability to hide code selectively makes your files more manageable and easier to read. 詳細については、「[アウトライン](/visualstudio/ide/outlining)」を参照してください。

`#Region` directives support code block semantics such as `#If...#End If`. This means they cannot begin in one block and end in another; the start and end must be in the same block. `#Region` directives are not supported within functions.

## <a name="to-collapse-and-hide-a-section-of-code"></a>To collapse and hide a section of code

Place the section of code between the `#Region` and `#End Region` statements, as in the following example:

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed. `#Region` blocks can also be nested within other `#Region` blocks.

> [!NOTE]
> Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.

## <a name="see-also"></a>関連項目

- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [アウトライン](/visualstudio/ide/outlining)
