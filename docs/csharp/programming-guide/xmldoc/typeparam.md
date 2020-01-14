---
title: <typeparam> - C# プログラミング ガイド
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 04145b82cbed0e9a5cae38ff9ef33d061ee792c9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694531"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam> (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>パラメーター  
 `name`  
 型パラメーターの名前。 名前は二重引用符 (" ") で囲みます。  
  
 `description`  
 型パラメーターの説明。  
  
## <a name="remarks"></a>Remarks  
 `<typeparam>` タグは、型パラメーターを説明するためにジェネリック型またはメソッドの宣言のコメントで使用する必要があります。 ジェネリック型またはメソッドの型パラメーターごとにタグを追加します。  
  
 詳細については、「[ジェネリック](../generics/index.md)」を参照してください。  
  
 `<typeparam>` タグのテキストは、IntelliSense、[オブジェクト ブラウザー ウィンドウ](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)、コード コメント Web レポートに表示されます。  
  
 コンパイル時に [-doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../../language-reference/index.md)
- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメントとして推奨されるタグ](./recommended-tags-for-documentation-comments.md)
