---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: e4beb320b3aa0cadb790dd3ab92255496bc32f05
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843839"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Visual Basic で宣言されている外部プロシージャの外部名に基づいて、.NET Framework の規則に従って文字列をマーシャ リングする必要がありますを指定します。  
  
 プロジェクトの外部で定義されたプロシージャを呼び出すときに、Visual Basic コンパイラには、プロシージャを正しく呼び出す必要があります情報へのアクセスはありません。 この情報には、プロシージャがある場所は、識別方法、その呼び出し元のシーケンスおよび戻り値の型が含まれます。 して、使用する文字列の文字セットします。 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)外部プロシージャへの参照を作成し、このために必要な情報を提供します。  
  
 `charsetmodifier`パーツ、`Declare`ステートメントが外部プロシージャの呼び出し中に文字列をマーシャ リングするための文字セットの情報を提供します。 また、Visual Basic が外部プロシージャ名の外部のファイルを検索する方法も影響します。 `Auto`修飾子は、Visual Basic が .NET Framework の規則に従って文字列をマーシャ リングして、場合によって、実行時プラットフォームの設定の基本文字を決定する必要があります最初を検索する場合、外部プロシージャ名を変更する必要がありますを指定します。失敗します。 詳細についてを参照してください「の文字セット」 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)します。  
  
 文字セットに修飾子が指定されていない場合`Ansi`既定値です。  
  
## <a name="remarks"></a>Remarks  
 `Auto`修飾子は、このコンテキストで使用できます。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>スマート デバイスの開発者向け注意事項  
 このキーワードはサポートされていません。  
  
## <a name="see-also"></a>関連項目

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
