---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: d8efd2359ecb65bec1b427d8b1dca4b0c88a1152
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469028"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)
説明内のテキストがコードであることを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---|---|  
|`text`|コードとして指定するテキストです。|  
  
## <a name="remarks"></a>コメント  
 `<c>`タグを使用する方法を示す説明内のテキストをコードとしてマークする必要があります。 複数行をコードとして指定する場合は、[\<code>](../../../visual-basic/language-reference/xmldoc/code.md) タグを使用します。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<c>`ことを示す [概要] セクションでタグ`Counter`コードに示します。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>関連項目
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
