---
title: My.Response オブジェクト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 5677108ac31733577915e15972386d8de5ccba49
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203351"
---
# <a name="myresponse-object"></a>My.Response オブジェクト
取得、<xref:System.Web.HttpResponse>オブジェクトに関連付けられている、<xref:System.Web.UI.Page>します。 このオブジェクトでは、HTTP 応答データをクライアントに送信し、その応答に関する情報を含めることができます。  
  
## <a name="remarks"></a>Remarks  
 `My.Response`オブジェクトには、現在が含まれています。<xref:System.Web.HttpResponse>ページに関連付けられているオブジェクト。  
  
 `My.Response`オブジェクトが使用できるだけ[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]アプリケーション。  
  
## <a name="example"></a>例  
 次の例からヘッダーのコレクションを取得、`My.Request`オブジェクトと使用、 `My.Response` ASP.NET ページに書き込むオブジェクト。  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Web.HttpResponse>
- [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)
