---
title: XML ファイルの処理
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 4230fd88b4b60c631135f5b7fb15f4b6272b5351
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347299"
---
# <a name="processing-the-xml-file-visual-basic"></a>XML ファイルの処理 (Visual Basic)
コンパイラは、ドキュメントを生成するためにタグ付けされたコードのコンストラクトごとに、ID 文字列を生成します。 (For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct. Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.  
  
 The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.  
  
 コンパイラは、次の規則に基づいて ID 文字列を生成します。  
  
- 文字列に空白は配置されません。  
  
- ID 文字列の最初の部分は、単一の文字とそれに続くコロンで識別されるメンバーの種類を示します。 The following member types are used.  
  
|文字|説明|  
|---|---|  
|N|名前空間<br /><br /> You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.|  
|T|type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|field: `Dim`|  
|P|property: `Property` (including default properties)|  
|M|method: `Sub`, `Function`, `Declare`, `Operator`|  
|E|event: `Event`|  
|!|エラー文字列<br /><br /> あとに続く文字列で、エラーの情報を示します。 The Visual Basic compiler generates error information for links that cannot be resolved.|  
  
- The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace. The name of the item, its enclosing type(s), and the namespace are separated by periods. If the name of the item itself contains periods, they are replaced by the number sign (#). It is assumed that no item has a number sign directly in its name. For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.  
  
- プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。 引数がない場合は、かっこはありません。 引数はコンマで区切られます。 The encoding of each argument follows directly how it is encoded in a .NET Framework signature.  
  
## <a name="example"></a>例  
 The following code shows how the ID strings for a class and its members are generated.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>関連項目

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
