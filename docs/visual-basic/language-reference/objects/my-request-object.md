---
title: My.Request オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 08212dc5fe563ce84be02ab706b56195a0636894
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836624"
---
# <a name="myrequest-object"></a>My.Request オブジェクト
要求されたページの <xref:System.Web.HttpRequest> オブジェクトを取得します。  
  
## <a name="remarks"></a>Remarks  
 `My.Request` オブジェクトには、現在の HTTP 要求に関する情報が含まれています。  
  
 `My.Request` オブジェクトは、ASP.NET アプリケーションでのみ使うことができます。  
  
## <a name="example"></a>例  
 次の例からヘッダーのコレクションを取得、`My.Request`オブジェクトと使用、 `My.Response` ASP.NET ページに書き込むオブジェクト。  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Web.HttpRequest>
- [My.Response オブジェクト](../../../visual-basic/language-reference/objects/my-response-object.md)
