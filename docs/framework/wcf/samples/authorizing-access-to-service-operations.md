---
title: サービス操作へのアクセスの承認
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 0bb4ae5ee0e21b6d226240ad84fcb35dcda8c4ee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189444"
---
# <a name="authorizing-access-to-service-operations"></a>サービス操作へのアクセスの承認
このサンプルで使用する方法、 [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)の使用を有効にする、<xref:System.Security.Permissions.PrincipalPermissionAttribute>サービス操作へのアクセスを承認する属性。 このサンプルがに基づいて、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)サンプル。 サービスとクライアントが構成を使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)します。 `mode`の属性、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)に設定されている`Message`と`clientCredentialType`に設定されている`Windows`します。 <xref:System.Security.Permissions.PrincipalPermissionAttribute> は各サービス メソッドに適用され、各操作へのアクセスを制限するために使用されます。 呼び出し元は、各操作にアクセスできる Windows 管理者である必要があります。  
  
 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービス構成ファイルを使用して、 [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を設定する、`principalPermissionMode`属性。  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 `principalPermissionMode` を `UseWindowsGroups` に設定すると、Windows グループ名に基づいて <xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用できるようになります。  
  
 呼び出し元が Windows 管理者グループのメンバーであることを要求するため、<xref:System.Security.Permissions.PrincipalPermissionAttribute> が各操作に適用されます。次のサンプル コードを参照してください。  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントが管理者グループのメンバーであるアカウントで実行される場合、クライアントは各操作と正常に通信できます。それ以外のアカウントで実行される場合、アクセスは拒否されます。 承認エラーを試すには、管理グループのメンバーではないアカウントでクライアントを実行します。 クライアントをシャットダウンするには、コンソール ウィンドウで Enter キーを押します。  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> を実装すると、サービスに承認エラーを通知することができます。 参照してください[拡張コントロール経由でエラー処理とレポート](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)実装について`IErrorHandler`します。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
