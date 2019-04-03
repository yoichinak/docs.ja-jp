---
title: Visual Basic における文字列操作メソッドの種類
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 44eb101ebdfeb316958a659107190ef1fc84df44
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821154"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic における文字列操作メソッドの種類
いくつかの方法を分析し、文字列の操作があります。 Visual Basic 言語の一部である一部のメソッドと他のユーザーに固有では、`String`クラス。  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic 言語と .NET Framework  
 Visual Basic のメソッドは、言語固有の関数として使用されます。 付けず、コードで使用することです。 次の例は、Visual Basic の文字列操作コマンドの一般的な使用を示しています。  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 この例で、`Mid`関数で直接操作を実行する`aString`に値が割り当てられます`bString`します。  
  
 Visual Basic の文字列操作メソッドの一覧は、次を参照してください。[文字列操作の概要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)します。  
  
### <a name="shared-methods-and-instance-methods"></a>共有メソッドとインスタンス メソッド  
 メソッドを使って、文字列を操作することも、`String`クラス。 内のメソッドの 2 種類があります`String`:*共有*メソッドと*インスタンス*メソッド。  
  
#### <a name="shared-methods"></a>共有メソッド  
 共有メソッドに由来するメソッド、`String`クラス自体と、操作するには、そのクラスのインスタンスは必要ありません。 これらのメソッドは、クラスの名前で修飾することができます (`String`) のインスタンスではなく、`String`クラス。 例:  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 上記の例では、<xref:System.String.Copy%2A?displayProperty=nameWithType>メソッドは静的メソッドを式に対して機能することが指定され、その結果の値を割り当てます`bString`します。  
  
#### <a name="instance-methods"></a>インスタンス メソッド  
 インスタンス メソッド、の特定のインスタンスからこれに対し、語幹`String`インスタンス名で修飾する必要があります。 例:  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 この例で、<xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドは、メソッドのインスタンスの`String`(つまり、 `aString`)。 操作の実行`aString`にその値を割り当てます`bString`します。  
  
 詳細については、ドキュメントを参照して、<xref:System.String>クラス。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
