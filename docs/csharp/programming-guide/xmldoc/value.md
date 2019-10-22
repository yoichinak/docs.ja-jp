---
title: <value> - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 09577d931c6b1f571cd4112c788da38bab85bf42
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523281"
---
# <a name="value-c-programming-guide"></a>\<value> (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>パラメーター  
 `property-description`  
 プロパティの説明。  
  
## <a name="remarks"></a>解説  
 \<value> タグを使用して、プロパティが表す値を記述することができます。 Visual Studio .NET 開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](./summary.md) タグが追加されることに注意してください。 その後、手動で \<value> タグを追加してプロパティが表す値を記述する必要があります。  
  
 コンパイル時に [-doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメントとして推奨されるタグ](./recommended-tags-for-documentation-comments.md)
