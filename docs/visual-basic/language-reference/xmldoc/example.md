---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8d1c2a958fa148238eaeedb9c2af3df2cb86d33d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502606"
---
# <a name="example-visual-basic"></a>\<example> (Visual Basic)
メンバーの例を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>パラメーター  
 `description`  
 コード例の説明です。  
  
## <a name="remarks"></a>コメント  
 `<example>`タグを使用して、メソッド、またはその他のライブラリ メンバーを使用する方法の例を指定できます。 一般的に、[\<code>](../../../visual-basic/language-reference/xmldoc/code.md) タグが使用されます。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<example>`タグを含める例を使用するために、`ID`フィールド。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>関連項目
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
