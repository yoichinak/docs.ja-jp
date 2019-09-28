---
title: XML コメントの例外には 'cref' 属性を指定しなければなりません
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592038"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML コメントの例外には 'cref' 属性を指定しなければなりません
@No__t 0exception > タグは、メソッドによってスローされる可能性のある例外を文書化する方法を提供します。 必須の `cref` 属性は、ドキュメントジェネレーターによってチェックされるメンバーの名前を指定します。 メンバーが存在する場合は、ドキュメントファイル内の正規要素名に変換されます。  
  
 **エラー ID:** BC42319  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 次のように、例外に `cref` 属性を追加します。  
  
    xml  
    ' ' ' の<exception cref="member">説明</exception>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
