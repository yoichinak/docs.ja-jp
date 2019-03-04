---
title: '方法: foreach を使用してコマンド ライン引数にアクセスする - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 5813ad573e89886ba991ca8cbcebb7232af05821
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971677"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>方法: foreach を使用してコマンド ライン引数にアクセスする (C# プログラミング ガイド)
配列の反復処理には、この例で示すように [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを使用する方法もあります。 `foreach` ステートメントは、配列、.NET Framework コレクション クラス、または <xref:System.Collections.IEnumerable> インターフェイスを実装する任意のクラスや構造体の反復処理に使用できます。  
  
> [!NOTE]
>  Visual Studio でアプリケーションを実行する場合、「[[デバッグ] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/debug-page-project-designer)」のコマンド ライン引数を指定できます。  
  
## <a name="example"></a>例  
 この例では、`foreach` を使用したコマンド ライン引数の出力方法を示します。  
  
 [!code-csharp[csProgGuideMain#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class2.cs#10)]  
  
 [!code-csharp[csProgGuideMain#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#11)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Array>
- <xref:System.Collections>
- [csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)
- [Main() とコマンドライン引数](../../../csharp/programming-guide/main-and-command-args/index.md)
- [方法: コマンド ライン引数を表示する](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Main() の戻り値](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
