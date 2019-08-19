---
title: My.settings オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: a50701998011c25c600c2a3763459c1aba3cc59a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567454"
---
# <a name="myresponse-object"></a>My.Response オブジェクト
に関連付けられた<xref:System.Web.HttpResponse>オブジェクトを取得します。 <xref:System.Web.UI.Page> このオブジェクトでは、HTTP 応答データをクライアントに送信し、その応答に関する情報を含めることができます。  
  
## <a name="remarks"></a>Remarks  
 オブジェクト`My.Response`には、ページ<xref:System.Web.HttpResponse>に関連付けられている現在のオブジェクトが格納されます。  
  
 オブジェクト`My.Response`は、ASP.NET アプリケーションでのみ使用できます。  
  
## <a name="example"></a>例  
 次の例では、 `My.Request`オブジェクトからヘッダーコレクションを取得し、 `My.Response`オブジェクトを使用して ASP.NET ページに書き込みます。  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Web.HttpResponse>
- [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)
