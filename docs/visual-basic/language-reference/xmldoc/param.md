---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4bcfe96361de9e196cb684ac4ba734f82442e25c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825561"
---
# <a name="param-visual-basic"></a>\<param > (Visual Basic)
パラメーターの名前と説明を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>パラメーター  
 `name`  
 メソッド パラメーターの名前です。 名前は二重引用符 (" ") で囲みます。  
  
 `description`  
 パラメーターの説明です。  
  
## <a name="remarks"></a>Remarks  
 `<param>`タグは、メソッドのパラメーターのいずれかを説明するメソッド宣言のコメントで使用する必要があります。  
  
 テキスト、`<param>`タグは、次の場所に表示されます。  
  
-   IntelliSense のパラメーター情報。 詳細については、「[IntelliSense の使用](/visualstudio/ide/using-intellisense)」を参照してください。  
  
-   オブジェクト ブラウザー。 詳細については、「[コードの構造の表示](/visualstudio/ide/viewing-the-structure-of-code)」を参照してください。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<param>`を記述するタグ、`id`パラメーター。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
