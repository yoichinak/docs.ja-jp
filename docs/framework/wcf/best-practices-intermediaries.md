---
title: ベスト プラクティス:中継局
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 0bd553486bfb89a0ec14c42a1bb7d2ed9c4c540d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131730"
---
# <a name="best-practices-intermediaries"></a>ベスト プラクティス:中継局
中継局のサービス側のチャネルが適切に閉じられていることを確認するために中継局を呼び出すときは、エラーが正しく処理されるよう注意する必要があります。  
  
 次に例を示します。 クライアントが中継局を呼び出すと、中継局はバックエンド サービスを呼び出します。  バックエンド サービスはエラー コントラクトを定義しないので、そのサービスからスローされるエラーはすべて型指定されていないエラーとして扱われます。  バックエンド サービスがスローされます、 <xref:System.ApplicationException> WCF が正しく、サービス側チャネルを中止します。 <xref:System.ApplicationException> が <xref:System.ServiceModel.FaultException> として中継局にスローされます。 中継局は <xref:System.ApplicationException> を再スローします。 WCF はこれを中継局からの型指定されていないエラーとして解釈し、クライアントに転送します。 エラーを受け取ると、中継局とクライアントのクライアント側チャネルはエラーを示します。 ただし、WCF にはエラーが致命的であることが通知されていないため、中継局のサービス側チャネルは開いたままです。  
  
 このシナリオのベスト プラクティスとしては、次のコード スニペットに示すように、サービスからスローされたエラーが致命的かどうかを検出し、致命的である場合は、中継局のサービス側チャネルでエラーを示します。  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [WCF エラー処理](../../../docs/framework/wcf/wcf-error-handling.md)
- [コントラクトおよびサービスのエラーの指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
