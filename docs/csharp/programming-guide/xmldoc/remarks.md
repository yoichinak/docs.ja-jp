---
title: <remarks> - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 822ca8feafe48402f8217c10ef37fcdb1576c27a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587754"
---
# <a name="remarks-c-programming-guide"></a>\<remarks> (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>parameters  
 `Description`  
 メンバーの説明。  
  
## <a name="remarks"></a>解説  
 \<remarks> タグを使用して、型の情報を追加し、[\<summary>](./summary.md) で指定された情報を補足します。 この情報はオブジェクト ブラウザー ウィンドウに表示されます。  
  
 コンパイル時に [/doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメントとして推奨されるタグ](./recommended-tags-for-documentation-comments.md)
