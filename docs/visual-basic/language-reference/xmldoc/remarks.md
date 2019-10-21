---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 38549b2fcce0740b2b9cfd42d950e56b343e7a30
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524670"
---
# <a name="remarks-visual-basic"></a>\<remarks > (Visual Basic)
メンバーの解説セクションを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>パラメーター  
 `description`  
 メンバーの説明。  
  
## <a name="remarks"></a>Remarks  
 @No__t_0 タグを使用して、 [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md)で指定された情報を補足する、型に関する情報を追加します。  
  
 この情報はオブジェクトブラウザーに表示されます。 オブジェクトブラウザーの詳細については、「[コードの構造の表示](/visualstudio/ide/viewing-the-structure-of-code)」を参照してください。  
  
 コンパイル時に [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<remarks>` タグを使用して、`UpdateRecord` メソッドの動作を説明します。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
