---
title: <list> - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: aadb24c43d49acb3e71490efd156b14d9fc5f133
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587973"
---
# <a name="list-c-programming-guide"></a>\<list> (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
## <a name="parameters"></a>parameters  
 `term`  
 定義される用語であり、`description` で定義されます。  
  
 `description`  
 行頭文字または番号付きリストの項目、または `term` の定義です。  
  
## <a name="remarks"></a>解説  
 \< > ブロックを使用して、テーブルまたは定義の一覧の見出し行を定義します。 テーブルを定義するときにのみ、見出しの用語のエントリを指定する必要があります。  
  
 リスト内の各項目は、\<item> ブロックで指定されます。 定義リストを作成する場合は、`term` と `description` の両方を指定する必要があります。 ただし、テーブル、箇条書きリスト、または番号付きリストの場合は、`description` のエントリを指定するだけで済みます。  
  
 リストまたはテーブルでは、必要な数の \<item> ブロックを使用できます。  
  
 コンパイル時に [/doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメントとして推奨されるタグ](./recommended-tags-for-documentation-comments.md)
