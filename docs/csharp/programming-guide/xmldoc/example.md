---
title: <example> - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: e81a95102100d3b0f3fdc84cf2113abf6ae35351
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588128"
---
# <a name="example-c-programming-guide"></a>\<example> (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>parameters  
 `description`  
 コード例の説明です。  
  
## <a name="remarks"></a>解説  
 \<example> タグでは、メソッドまたはその他のライブラリ メンバーの使用例を指定できます。 一般的に、[\<code>](./code.md) タグが使用されます。  
  
 コンパイル時に [/doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメントとして推奨されるタグ](./recommended-tags-for-documentation-comments.md)
