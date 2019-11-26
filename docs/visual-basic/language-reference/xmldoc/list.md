---
title: <list>
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: db5c571d2f2c59419c886f6596f4e4dbd30d7baf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352318"
---
# <a name="list-visual-basic"></a>\<list> (Visual Basic)
Defines a list or table.  
  
## <a name="syntax"></a>構文  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a>パラメーター  
 `type`  
 The type of the list. Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.  
  
 `term`  
 Only used when `type` is "table." A term to define, which is defined in the description tag.  
  
 `description`  
 When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.  
  
## <a name="remarks"></a>Remarks  
 The `<listheader>` block defines the heading of either a table or definition list. When defining a table, you only have to supply an entry for `term` in the heading.  
  
 Each item in the list is specified with an `<item>` block. When creating a definition list, you must specify both `term` and `description`. However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.  
  
 A list or table can have as many `<item>` blocks as needed.  
  
 コンパイル時に [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 This example uses the `<list>` tag to define a bulleted list in the remarks section.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
