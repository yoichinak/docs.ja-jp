---
title: ドキュメント コメント用の推奨タグ - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 963be5273389ebbdb3458d41b0658de0d94bb2cd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634796"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>ドキュメント コメント用の推奨タグ (C# プログラミング ガイド)
コード内のドキュメント コメントは、C# コンパイラによって処理され、**/doc** コマンド ライン オプションで指定した名前のファイルに XML 形式で出力されます。 コンパイラによって生成されたファイルに基づいて最終的なドキュメントを作成するには、カスタム ツールを作成するか、[DocFX](https://dotnet.github.io/docfx/) や [Sandcastle](https://github.com/EWSoftware/SHFB) などのツールを使用します。  
  
 タグは、型や型メンバーなどのコード コンストラクターに対して処理されます。  
  
> [!NOTE]
>  ドキュメント コメントは、名前空間に適用できません。  
  
 コンパイラは、有効な XML のタグをすべて処理します。 ユーザー ドキュメントで一般的に使用される機能を提供するタグを次の表に示します。  
  
## <a name="tags"></a>Tags  
  
||||  
|---|---|---|  
|[\<c>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para>](../../../csharp/programming-guide/xmldoc/para.md)|[\<see>](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<code>](../../../csharp/programming-guide/xmldoc/code.md)|[\<param>](../../../csharp/programming-guide/xmldoc/param.md)*|[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<example>](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref>](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<summary>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<include>](../../../csharp/programming-guide/xmldoc/include.md)*|[\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<list>](../../../csharp/programming-guide/xmldoc/list.md)|[\<returns>](../../../csharp/programming-guide/xmldoc/returns.md)|[\<value>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* は、コンパイラが構文を検証することを示します。)  
  
 ドキュメント コメントのテキストに山かっこを表示する場合は、次の例に示すように `<` と `>` を使用します。  
  
```csharp  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [/doc (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [XML ドキュメント コメント](../../../csharp/programming-guide/xmldoc/index.md)
