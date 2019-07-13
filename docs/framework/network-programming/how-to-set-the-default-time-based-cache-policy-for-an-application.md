---
title: '方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: 99f9905109a4deabe3cfb2e3616913e84f565cb7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299125"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する
既定の時間ベースのキャッシュ ポリシーにより、キャッシュされたリソースと共に送信されるヘッダーによってアプリケーションでキャッシュの動作を定義することができます。RFC 2616 のセクション 13 と 14 で定義されているキャッシュの動作については、[Internet Engineering Task Force (IETF)](https://www.ietf.org/) に関するページをご覧ください。 これは、ほとんどのアプリケーションの適切なキャッシュの動作です。  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>アプリケーションの既定の自動ポリシーを設定するには  
  
1. 既定の時間ベースのポリシー オブジェクトを作成します。  
  
2. アプリケーション ドメインの既定値として、ポリシー オブジェクトを設定します。  
  
## <a name="example"></a>例  
 このセクションの 2 つの例では、同一のポリシーを生成します。  
  
 次の例では、既定の時間ベースのポリシーを作成し、アプリケーション ドメインの既定値として設定します。  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 次の例に示すように、<xref:System.Net.Cache.RequestCachePolicy> クラスを使用して既定の時間ベースのキャッシュ ポリシーを作成することもできます。  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a>関連項目

- [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)
- [場所ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
