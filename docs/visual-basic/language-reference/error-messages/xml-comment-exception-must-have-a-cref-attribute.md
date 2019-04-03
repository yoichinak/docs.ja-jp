---
title: XML コメントの例外には 'cref' 属性を指定しなければなりません
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: a974df5d2305b88946981d0d258a8088b23d3fc3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813289"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML コメントの例外には 'cref' 属性を指定しなければなりません
\<例外 > タグは、メソッドによってスローされる可能性が例外を文書化する方法を提供します。 必要な`cref`属性は、ドキュメントのジェネレーターがチェックされているメンバーの名前を指定します。 メンバーが存在する場合は、ドキュメント ファイルで正規要素名に変換されます。  
  
 **エラー ID:** BC42319  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   追加、`cref`属性、例外を次のようにします。  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>関連項目

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [方法: XML ドキュメントを作成します。](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
