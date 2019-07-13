---
title: XML の使用によるコードのドキュメントの作成 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 6b9fe9994b7bdf2259dcdb1ecef906e0f9955c8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785503"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>XML の使用によるコードのドキュメントの作成 (Visual Basic)

Visual basic で XML を使用してコードを文書化します。

## <a name="xml-documentation-comments"></a>XML ドキュメントのコメント

Visual Basic では、プロジェクトの XML ドキュメントを自動的に作成する簡単な方法を提供します。 型とメンバーの XML スケルトンが自動的に生成し、パラメーターごとに、その他の注釈の概要、説明的なドキュメントを提供できます。 適切なセットアップで、プロジェクトと .xml 拡張子と同じ名前を持つ XML ファイルに XML ドキュメントは自動的に生成されます。 詳細については、「[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。

XML ファイルを使用またはそれ以外の場合、XML として操作できます。 このファイルは、プロジェクトの出力の .exe または .dll ファイルと同じディレクトリにあります。

XML ドキュメントの先頭`'''`します。 これらのコメントの処理にはいくつか制限があります。

- ドキュメントは整形式の XML である必要があります。 XML の形式が正しくない場合、は、警告が生成され、ドキュメント ファイルにエラーが発生したことを示すコメントが含まれています。

- 開発者は、独自のタグ セットを自由に作成できます。 推奨されるタグ (このトピックの「関連項目」を参照してください) 設定があります。 推奨されるタグの一部には特別な意味があります。

  - \<param> タグは、パラメーターの記述に使われます。 このタグがあると、コンパイラは、パラメーターが存在すること、およびすべてのパラメーターがドキュメントで記述されていることを確認します。 検証に失敗した場合、コンパイラは警告を発行します。

  - `cref` 属性は任意のタグにアタッチでき、コード要素への参照を提供します。 コンパイラは、このコード要素が存在することを確認します。 検証に失敗した場合、コンパイラは警告を発行します。 いずれかは、コンパイラもは`Imports`ステートメントで示される型を検索するときに、`cref`属性。

  - \<概要 > タグは、型またはメンバーに関する情報を表示する Visual Studio での IntelliSense によって使われます。

## <a name="related-sections"></a>関連項目

ドキュメントのコメントで XML ファイルを作成する方法については、次のトピックを参照してください。

- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)

- [XML ファイルの処理](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [方法: XML ドキュメントを作成します。](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Visual Studio の XML ツール](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>関連項目

- [Visual Basic でのアプリケーションの開発](../../../visual-basic/developing-apps/index.md)
- [Visual Basic プログラミング ガイド](../../../visual-basic/programming-guide/index.md)
