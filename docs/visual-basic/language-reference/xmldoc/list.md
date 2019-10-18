---
title: <list> (Visual Basic)
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
ms.openlocfilehash: 5d4295d485611e75e8b6c8d8f95e079654f0cfa3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524749"
---
# <a name="list-visual-basic"></a>\<list > (Visual Basic)
リストまたはテーブルを定義します。  
  
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
 リストの型。 箇条書きの場合は "箇条書き"、番号付きリストの場合は "数値"、2列テーブルの場合は "table" にする必要があります。  
  
 `term`  
 @No__t_0 が "table" の場合にのみ使用されます。 Description タグで定義されている定義対象の用語。  
  
 `description`  
 @No__t_0 が "bullet" または "number" の場合、`description` は `type` が "table" の場合はリスト内の項目であり、`description` は `term` の定義です。  
  
## <a name="remarks"></a>Remarks  
 @No__t_0 ブロックでは、テーブルまたは定義リストの見出しを定義します。 テーブルを定義する場合は、見出しに `term` のエントリを指定するだけで済みます。  
  
 リスト内の各項目には、`<item>` ブロックが指定されています。 定義リストを作成する場合は、`term` と `description` の両方を指定する必要があります。 ただし、テーブル、箇条書きリスト、番号付きリストの場合は、`description` のエントリを指定するだけで済みます。  
  
 リストまたはテーブルには、必要に応じて `<item>` ブロックをいくつでも含めることができます。  
  
 コンパイル時に [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<list>` タグを使用して、「解説」で箇条書きリストを定義します。  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
