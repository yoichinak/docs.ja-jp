---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 531cac9bfec24577c22cb52962b2ac1eb740c5c8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975499"
---
# <a name="summary-visual-basic"></a>\<概要 > (Visual Basic)
メンバーの概要を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `description`  
 オブジェクトの概要。  
  
## <a name="remarks"></a>Remarks  
 使用して、`<summary>`型または型のメンバーを記述するタグ。 型の説明に補足情報を追加するには、[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) タグを使用します。  
  
 テキスト、`<summary>`タグは IntelliSense の型に関する情報の唯一のソースであり、オブジェクト ブラウザーにも表示されます。 オブジェクト ブラウザーの詳細については、次を参照してください。[コードの構造を表示する](/visualstudio/ide/viewing-the-structure-of-code)します。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<summary>`を記述するタグ、`ResetCounter`メソッドと`Counter`プロパティ。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>関連項目
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
