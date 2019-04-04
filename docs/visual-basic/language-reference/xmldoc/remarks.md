---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c5c088472ae09a416953d9c0829cad1cb48646b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833491"
---
# <a name="remarks-visual-basic"></a>\<remarks > (Visual Basic)
メンバーの「解説」セクションをを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>パラメーター  
 `description`  
 メンバーの説明。  
  
## <a name="remarks"></a>Remarks  
 使用して、`<remarks>`で指定された情報を補うため、型に関する情報を追加するタグ[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)します。  
  
 この情報は、オブジェクト ブラウザーに表示されます。 オブジェクト ブラウザーの詳細については、[コードの構造を表示する](/visualstudio/ide/viewing-the-structure-of-code)を参照してください。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<remarks>`何かを説明するタグ、`UpdateRecord`メソッドします。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
