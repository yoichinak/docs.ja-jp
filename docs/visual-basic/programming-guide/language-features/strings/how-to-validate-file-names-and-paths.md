---
title: '方法: ファイル名と Visual Basic でのパスを検証します。'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: c8e01a0f5a3f99fdbc424d6cd7d224367c7bad08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032176"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>方法: ファイル名と Visual Basic でのパスを検証します。
この例を返します、`Boolean`文字列が、ファイル名またはパスを表すかどうかを示す値です。 ファイル システムで許可されていない文字が名前に含まれるかどうか、検証を確認します。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 この例では、名前が正常に配置され、コロン、またはディレクトリ名がない場合、または名前の長さがシステム定義の最大長を超える場合はチェックしません。 チェックされません、アプリケーションが、指定した名前のファイル システム リソースにアクセスする権限を持つかどうかです。  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
