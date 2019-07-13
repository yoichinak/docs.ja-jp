---
title: '&lt;code&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 8a4708a7b50b0e221c1ebe7f95d4f8ff80cd1ebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566308"
---
# <a name="ltcodegt-visual-basic"></a>&lt;code&gt;(Visual Basic)
テキストが複数行のコードであることを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `content`  
 コードとしてマークするテキスト。  
  
## <a name="remarks"></a>コメント  
 コードとして複数の行を示すには、`<code>`タグを使用します。 説明内のテキストをコードとしてマークする場合は、[\<c](../../../visual-basic/language-reference/xmldoc/c.md) タグを使用します。    
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、\<code> タグを使用するためのサンプル コードを`ID`フィールド。  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a>関連項目
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
