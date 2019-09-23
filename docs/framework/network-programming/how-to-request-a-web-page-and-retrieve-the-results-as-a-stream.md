---
title: '方法: Web ページを要求し、ストリームとして結果を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: b3d24a958ec93084d03d2ad2e0eb6d9d2507e155
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048175"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>方法: Web ページを要求し、ストリームとして結果を取得する
この例では、Web ページを要求し、ストリームとして結果を取得する方法を示します。  
  
## <a name="example"></a>例  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- <xref:System.IO> 名前空間と <xref:System.Net> 名前空間への参照。  
  
## <a name="see-also"></a>関連項目

- [データの要求](requesting-data.md)
