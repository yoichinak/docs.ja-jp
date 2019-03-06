---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 670064084d3297a54b2860da3fe3acab00fa3ed8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469184"
---
# <a name="returns-visual-basic"></a>\<返します > (Visual Basic)
プロパティまたは関数の戻り値を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>パラメーター  
 `description`  
 戻り値の説明。  
  
## <a name="remarks"></a>Remarks  
 使用して、`<returns>`戻り値を記述するメソッド宣言のコメント内のタグ。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<returns>`何かを説明するタグ、`DoesRecordExist`関数が返される。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
