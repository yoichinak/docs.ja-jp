---
title: XML の使用によるコードのドキュメントの作成
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: bdf0da7a8acc919e4a1d66b81e30c9ed912dd321
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347441"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>XML の使用によるコードのドキュメントの作成 (Visual Basic)

In Visual Basic, you can document your code using XML

## <a name="xml-documentation-comments"></a>XML ドキュメントのコメント

Visual Basic provides an easy way to automatically create XML documentation for projects. You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks. With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension. 詳細については、「[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。

The XML file can be consumed or otherwise manipulated as XML. This file is located in the same directory as the output .exe or .dll file of your project.

XML documentation starts with `'''`. これらのコメントの処理にはいくつか制限があります。

- ドキュメントは整形式の XML である必要があります。 If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.

- 開発者は、独自のタグ セットを自由に作成できます。 There is a recommended set of tags (see "Related Sections" in this topic). 推奨されるタグの一部には特別な意味があります。

  - \<param> タグは、パラメーターの記述に使われます。 このタグがあると、コンパイラは、パラメーターが存在すること、およびすべてのパラメーターがドキュメントで記述されていることを確認します。 If the verification fails, the compiler issues a warning.

  - `cref` 属性は任意のタグにアタッチでき、コード要素への参照を提供します。 コンパイラは、このコード要素が存在することを確認します。 If the verification fails, the compiler issues a warning. The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.

  - The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.

## <a name="related-sections"></a>関連項目

For details on creating an XML file with documentation comments, see the following topics:

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)

- [XML ファイルの処理](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Visual Studio の XML ツール](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>関連項目

- [Visual Basic でのアプリケーションの開発](../../../visual-basic/developing-apps/index.md)
- [Visual Basic のプログラミング ガイド](../../../visual-basic/programming-guide/index.md)
