---
title: <permission> - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: e9eb50394f01072a194d3f746577707f89ba65dd
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587887"
---
# <a name="permission-c-programming-guide"></a>\<permission> (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>parameters  
 cref = "`member`"  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。 コンパイラは、指定されたコード要素が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。 *member* は、二重引用符 (" ") で囲む必要があります。  
  
 ジェネリック型への cref 参照を作成する方法については、「[\<see>](./see.md)」を参照してください。  
  
 `description`  
 メンバーへのアクセスの説明です。  
  
## <a name="remarks"></a>解説  
 \<permission> タグを使用すると、メンバーのアクセスを文書化できます。 <xref:System.Security.PermissionSet> クラスを使用すると、メンバーへのアクセスを指定できます。  
  
 コンパイル時に [/doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメントとして推奨されるタグ](./recommended-tags-for-documentation-comments.md)
