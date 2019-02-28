---
title: <include> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: bf7a434569bf82066c79962ae24741759b97e5ce
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973692"
---
# <a name="include-visual-basic"></a>\<含める > (Visual Basic)
型と、ソース コード内のメンバーを記述する別のファイルを参照します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>パラメーター  
 `filename`  
 必須。 文書を含むファイルの名前。 ファイル名をパスで修飾することができます。 囲む`filename`で二重引用符 ("")。  
  
 `tagpath`  
 必須。 タグ `name` につながる `filename` 内のタグのパス。 パスを二重引用符で囲みます ("")。  
  
 `name`  
 必須。 コメントの前にあるタグの名前指定子。 `Name` 必要があります、`id`します。  
  
 `id`  
 必須。 コメントの前に配置するタグの ID。 ID を単一引用符で囲みます (' ')。  
  
## <a name="remarks"></a>Remarks  
 使用して、`<include>`タグをソース コード内のメンバーと型を記述する別のファイル内のコメントを参照してください。 これは文書化のコメントをソース コード ファイル内に直接配置する方法の代替です。  
  
 `<include>`タグは、W3C XML Path Language (XPath) Version 1.0 』 を使用します。 カスタマイズする方法の詳細については、`<include>`を使用して、参照してください<https://www.w3.org/TR/xpath>します。  
  
## <a name="example"></a>例  
 この例では、`<include>`メンバー ドキュメントのコメントをという名前のファイルからインポートするタグ`commentFile.xml`します。  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 形式、`commentFile.xml`のとおりです。  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>関連項目
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
