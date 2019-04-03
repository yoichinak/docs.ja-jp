---
title: '方法: 文字列 (Visual Basic) 内の検索'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: b690aa78a2cf07b0db5bdd28d7d71ed4a79fbf61
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823299"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>方法: 文字列 (Visual Basic) 内の検索
この例では、<xref:System.String.IndexOf%2A>メソッドを<xref:System.String>部分文字列の最初に見つかった位置のインデックスを報告するオブジェクト。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `Imports`ステートメントの指定、<xref:System>名前空間。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 <xref:System.String.IndexOf%2A>メソッドは、最初に見つかった部分文字列の最初の文字の位置を報告します。 インデックスには文字列の最初の文字がインデックス 0 のことを意味する 0 から始まります。  
  
 場合<xref:System.String.IndexOf%2A>、部分文字列が見つからない-1 を返します。  
  
 <xref:System.String.IndexOf%2A>メソッドは大文字であり、現在のカルチャを使用します。  
  
 最適なエラーに制御するために文字列の検索をする可能性があります、`Try`のブロックを[お試しください.キャッチしてください.Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)構築します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [文字列](../../../../visual-basic/programming-guide/language-features/strings/index.md)
