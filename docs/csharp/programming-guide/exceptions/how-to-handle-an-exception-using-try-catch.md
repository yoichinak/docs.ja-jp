---
title: '方法: try-catch を使用して例外を処理する - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 5378de09962055fe7d2e100484ad69662c803e0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590241"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>方法: try/catch を使用して例外を処理する (C# プログラミング ガイド)
[try-catch](../../language-reference/keywords/try-catch.md) ブロックの目的は、作業コードによって生成された例外をキャッチし、処理することです。 例外によっては、`catch` ブロックで処理し、例外を再スローせずに問題を解決できるものもありますが、多くの場合、適切な例外がスローされるようにする必要があります。  
  
## <a name="example"></a>例  
 この例の <xref:System.IndexOutOfRangeException> は最も適切な例外というわけではありません。呼び出し元から `index` 引数が渡されてエラーが発生しているため、より適切なメソッドは <xref:System.ArgumentOutOfRangeException> になります。  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>説明  
 例外を発生させるコードは `try` ブロックに囲まれています。 `IndexOutOfRangeException` が発生した場合にこれを処理するための `catch` ステートメントが、すぐ後に追加されています。 `catch` ブロックは `IndexOutOfRangeException` を処理し、代わりにより適切な `ArgumentOutOfRangeException` 例外をスローします。 呼び出し元にできるだけ多くの情報を提供するため、元の例外を新しい例外の <xref:System.Exception.InnerException%2A> として指定することを検討してください。 <xref:System.Exception.InnerException%2A> プロパティは [readonly](../../language-reference/keywords/readonly.md) であるため、新しい例外のコンストラクターで割り当てる必要があります。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [例外と例外処理](./index.md)
- [例外処理](./exception-handling.md)
