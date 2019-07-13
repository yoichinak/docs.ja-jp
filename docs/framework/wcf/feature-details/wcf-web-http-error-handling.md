---
title: WCF Web HTTP エラー処理
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 491c39d97c48e2f92ff258ac42b9576d407b898e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648419"
---
# <a name="wcf-web-http-error-handling"></a>WCF Web HTTP エラー処理
Windows Communication Foundation (WCF) Web HTTP エラー処理を使用すると、HTTP ステータス コードを指定する操作 (たとえば、XML または JSON) と同じ形式を使用してエラーの詳細を返す WCF Web HTTP サービスからエラーが返されることができます。  
  
## <a name="wcf-web-http-error-handling"></a>WCF Web HTTP エラー処理  
 <xref:System.ServiceModel.Web.WebFaultException> クラスは、HTTP 状態コードを指定できるようにするコンストラクターを定義します。 この状態コードは、クライアントに返されます。 <xref:System.ServiceModel.Web.WebFaultException> クラスのジェネリック バージョンである <xref:System.ServiceModel.Web.WebFaultException%601> を使用すると、発生したエラーに関する情報を格納しているユーザー定義型を返すことができます。 このカスタム オブジェクトは、操作で定義された形式を使用してシリアル化され、クライアントに返されます。 次の例は、HTTP 状態コードを返す方法を示しています。  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 次の例は、HTTP 状態コードおよび追加情報をユーザー定義型で返す方法を示しています。 `MyErrorDetail` は、発生したエラーに関する追加情報を格納しているユーザー定義型です。  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 このコードは、禁止されている状態コード、および `MyErrorDetails` オブジェクトのインスタンスを格納している本文と共に、HTTP 応答を返します。 `MyErrorDetails` オブジェクトの形式は、次の値によって決まります。  
  
- サービス操作で指定された `ResponseFormat` 属性または <xref:System.ServiceModel.Web.WebGetAttribute> 属性の <xref:System.ServiceModel.Web.WebInvokeAttribute> パラメーターの値。  
  
- <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> の値。  
  
- <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> プロパティの値 (<xref:System.ServiceModel.Web.OutgoingWebResponseContext> にアクセスして取得)。  
  
 これらの値が、操作の書式設定に影響する方法の詳細については、次を参照してください。 [WCF Web HTTP 書式](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)します。  
  
 <xref:System.ServiceModel.Web.WebFaultException> は <xref:System.ServiceModel.FaultException> であるため、SOAP エンドポイントと Web HTTP エンドポイントを公開するサービスのエラー例外プログラミング モデルとして使用できます。  
  
## <a name="see-also"></a>関連項目

- [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF Web HTTP 形式](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [エラーの定義と指定](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [例外とエラーの処理](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [エラーの送受信](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
