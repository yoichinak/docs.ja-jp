---
title: XML コメントの例外には 'cref' 属性を指定しなければなりません
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321171"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML コメントの例外には 'cref' 属性を指定しなければなりません

@No__t 0exception > タグは、メソッドによってスローされる可能性のある例外を文書化する方法を提供します。 必須の `cref` 属性は、ドキュメントジェネレーターによってチェックされるメンバーの名前を指定します。 メンバーが存在する場合は、ドキュメントファイル内の正規要素名に変換されます。

**エラー ID:** BC42319

## <a name="to-correct-this-error"></a>このエラーを解決するには

次のように、例外に `cref` 属性を追加します。

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>関連項目

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
