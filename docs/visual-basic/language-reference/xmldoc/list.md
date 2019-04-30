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
ms.openlocfilehash: 7d7b85867f4c701322c5e6c31f2d89ab38fad05d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940880"
---
# <a name="list-visual-basic"></a>\<リスト > (Visual Basic)
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
 リストの型。 箇条書き、番号付きリスト、または 2 つの列のテーブルには、"table"の"number"の"bullet"があります。  
  
 `term`  
 場合のみ使用`type`"table"には 説明タグで定義されている用語を定義します。  
  
 `description`  
 ときに`type`"bullet"または"number" `description` 、リスト内の項目は、ときに`type`は"table"`description`の定義は、 `term`。  
  
## <a name="remarks"></a>Remarks  
 `<listheader>`ブロックは、テーブルまたは定義の一覧の見出しを定義します。 のみのエントリを指定する必要があるテーブルを定義するときに`term`見出し。  
  
 リスト内の各項目を指定した、`<item>`ブロックします。 定義リストを作成するときに、両方を指定する必要があります`term`と`description`します。 ただし、テーブル、箇条書きまたは番号付きリストだけであるエントリを指定する`description`します。  
  
 リストまたはテーブルとして多く持つことができます`<item>`に応じてをブロックします。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、 `<list>` 「解説」セクションで、箇条書きリストを定義するタグ。  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
