---
title: '方法: XML ドキュメントを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 41b7ef1f435fd0a4f20c4ca2936e2d91e155f7c5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347417"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>方法 : Visual Basic で XML ドキュメントを作成する

This example shows how to add XML documentation comments to your code.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>To create XML documentation for a type or member

1. In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.

2. Type `'''` (three single-quotation marks).

    An XML skeleton for the type or member is added in the **Code Editor**.

3. Add descriptive information between the appropriate tags.

    > [!NOTE]
    > If you add additional lines within the XML documentation block, each line must begin with `'''`.

4. Add additional code that uses the type or member with the new XML documentation comments.

    IntelliSense displays the text from the \<summary> tag for the type or member.

5. Compile the code to generate an XML file containing the documentation comments. 詳細については、「[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [XML の使用によるコードのドキュメントの作成](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
