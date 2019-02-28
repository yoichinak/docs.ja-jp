---
title: XML ファイルの処理 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 1cff4d72a294a4635df72dc91c46fa5da92aa388
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976201"
---
# <a name="processing-the-xml-file-visual-basic"></a>XML ファイルの処理 (Visual Basic)
コンパイラは、ドキュメントを生成するためにタグ付けされたコードのコンストラクトごとに、ID 文字列を生成します。 (コードをタグ付けする方法については、次を参照してください[XML コメント タグ](../../../visual-basic/language-reference/xmldoc/index.md)。)。ID 文字列によって、コンストラクトは一意に識別されます。 XML ファイルを処理するプログラムは、ID 文字列を使用して、対応するを識別するために[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メタデータ/リフレクション項目。  
  
 XML ファイルは、コードの階層表現ではありません。各要素に対して生成された ID を持つ単純なリストになります。  
  
 コンパイラは、次の規則に基づいて ID 文字列を生成します。  
  
-   文字列に空白は配置されません。  
  
-   ID 文字列の最初の部分は、単一の文字とそれに続くコロンで識別されるメンバーの種類を示します。 次のメンバーの種類が使用されます。  
  
|文字|説明|  
|---|---|  
|N|namespace<br /><br /> 名前空間をドキュメントのコメントを追加することはできませんが、それらへの CREF 参照を行うことができますが、サポートされています。|  
|T|型: `Class`、 `Module`、 `Interface`、 `Structure`、 `Enum`、 `Delegate`|  
|F|フィールド: `Dim`|  
|P|プロパティ: `Property` (既定のプロパティを含む)|  
|M|方法: `Sub`、 `Function`、 `Declare`、 `Operator`|  
|E|イベント: `Event`|  
|!|エラー文字列<br /><br /> あとに続く文字列で、エラーの情報を示します。 Visual Basic コンパイラでは、解決できないリンクのエラー情報を生成します。|  
  
-   2 番目の部分、 `String` 、名前空間のルートにある項目の完全修飾の名前を指定します。 項目、その外側の型および名前空間の名前は、ピリオドで区切られます。 シャープ記号で置き換えられますが、項目自体の名前にピリオドが含まれている場合 (#)。 項目の名前には番号記号がないことが前提です。 たとえば、完全修飾名の`String`コンス トラクターになる`System.String.#ctor`します。  
  
-   プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。 引数がない場合は、かっこはありません。 引数はコンマで区切られます。 エンコード方法に直接依存各引数のエンコーディングを[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]署名します。  
  
## <a name="example"></a>例  
 次のコードは、クラスの ID の文字列し、そのメンバーが生成されます。  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>関連項目
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [方法: XML ドキュメントを作成します。](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
