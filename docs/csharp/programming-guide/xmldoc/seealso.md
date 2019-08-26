---
title: <seealso> - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: 3ddaa7efec2b4bf5ffa53971aa6f380a1be9bad8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587664"
---
# <a name="seealso-c-programming-guide"></a>\<seealso> (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a>parameters  
 cref = "`member`"  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。 コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。`member` は二重引用符 (" ") で囲む必要があります。  
  
 ジェネリック型への cref 参照を作成する方法については、「[\<see>](./see.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 \<seealso > タグを使用して、「See Also」セクションに表示するテキストを指定することができます。 [\<see>](./see.md) タグを使用すると、テキスト内からリンクを指定できます。  
  
 コンパイル時に [/doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 \<seealso> の使用例については、[\<summary>](./summary.md) を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメントとして推奨されるタグ](./recommended-tags-for-documentation-comments.md)
