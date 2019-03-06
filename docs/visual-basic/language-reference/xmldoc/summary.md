---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: e629a738a706b09dec97dd6593ef493470ec9472
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473878"
---
# <a name="summary-visual-basic"></a>\<概要 > (Visual Basic)
メンバーの概要を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>パラメーター  
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
