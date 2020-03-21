---
title: サービス操作へのアクセスの承認
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: c2ad6977674666ef65df1ea4cfe58cfd4bff8b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183925"
---
# <a name="authorizing-access-to-service-operations"></a>サービス操作へのアクセスの承認
このサンプルでは[\<、serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を使用して、サービス操作へのアクセス<xref:System.Security.Permissions.PrincipalPermissionAttribute>を承認する属性の使用を有効にする方法を示します。 このサンプルは、[開始の](../../../../docs/framework/wcf/samples/getting-started-sample.md)サンプルに基づいています。 サービスとクライアントは[\<、wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を使用して構成されます。 セキュリティ`mode` [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)の属性が に設定され`Message`、`clientCredentialType`に`Windows`設定されています。 <xref:System.Security.Permissions.PrincipalPermissionAttribute> は各サービス メソッドに適用され、各操作へのアクセスを制限するために使用されます。 呼び出し元は、各操作にアクセスできる Windows 管理者である必要があります。  
  
 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービス構成ファイルは[\<、サービス認証>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を使用して属性`principalPermissionMode`を設定します。  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> を実装すると、サービスに承認エラーを通知することができます。 実装`IErrorHandler`の詳細については、「[エラー処理とレポートの制御の拡張](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)」を参照してください。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには、「 [Windows コミュニケーション ファウンデーション サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
