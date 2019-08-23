---
title: '方法: PrincipalPermissionAttribute クラスでアクセスを制限する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 3b109e3e6817c300af1e79258d555562dcba067a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951022"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>方法: PrincipalPermissionAttribute クラスでアクセスを制限する
Windows ドメイン コンピューターのリソースへのアクセスを制御することは、基本的なセキュリティ タスクです。 たとえば、給与情報のような機密データは、特定のユーザーだけが表示できるようにする必要があります。 ここでは、ユーザーが定義済みグループに属していることを要求することによって、メソッドへのアクセスを制限する方法について説明します。 実際のサンプルについては、「[サービス操作へのアクセスの承認](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)」を参照してください。  
  
 タスクは、2 つの別個の手順で構成されます。 最初の手順では、グループを作成してユーザーを追加します。 2 番目の手順では、グループを指定するために <xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスを適用します。  
  
### <a name="to-create-a-windows-group"></a>Windows グループを作成するには  
  
1. コンピューターの**管理**コンソールを開きます。  
  
2. 左側のパネルで、 **[ローカルユーザーとグループ]** をクリックします。  
  
3. **[グループ]** を右クリックし、 **[新しいグループ]** をクリックします。  
  
4. **[グループ名]** ボックスに、新しいグループの名前を入力します。  
  
5. **[説明]** ボックスに、新しいグループの説明を入力します。  
  
6. **[追加]** ボタンをクリックして、グループに新しいメンバーを追加します。  
  
7. 自分自身をグループに追加した場合は、次のコードをテストする前に、コンピューターからいったんログオフし、再度ログオンして自分自身をグループに含める必要があります。  
  
### <a name="to-demand-user-membership"></a>ユーザー メンバーシップを要求するには  
  
1. 実装されたサービスコントラクトコードを含む Windows Communication Foundation (WCF) コードファイルを開きます。 コントラクトの実装の詳細については、「[サービスコントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)」を参照してください。  
  
2. 特定のグループに制限される必要がある各メソッドに <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性を適用します。 <xref:System.Security.Permissions.SecurityAttribute.Action%2A> プロパティを <xref:System.Security.Permissions.SecurityAction.Demand> に設定し、<xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> プロパティをグループの名前に設定します。 例:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性をコントラクトに適用すると、<xref:System.Security.SecurityException> がスローされます。 この属性はメソッド レベルにのみ適用できます。  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>証明書を使用したメソッドへのアクセスの制御  
 クライアント資格情報の種類が "証明書" の場合は、`PrincipalPermissionAttribute` クラスを使用してメソッドへのアクセスを制御することもできます。 そのためには、証明書のサブジェクトと拇印が必要になります。  
  
 証明書のプロパティを調べるには、 [「方法:MMC スナップ](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)インを使用して証明書を表示します。 サムプリント値を調べるには[、「方法:証明書](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)の拇印を取得します。  
  
#### <a name="to-control-access-using-a-certificate"></a>証明書を使用してアクセスを制御するには  
  
1. アクセスを制限するメソッドに <xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスを適用します。  
  
2. 属性のアクションを <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType> に設定します。  
  
3. `Name` プロパティを、サブジェクト名と証明書の拇印で構成される文字列に設定します。 次の例に示すように、2 つの値をセミコロンと空白で区切ってください。  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. 次の構成例に示すように、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> プロパティを <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> に設定します。  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     この値を `UseAspNetRoles` に設定すると、`Name` の `PrincipalPermissionAttribute` プロパティを使用して文字列が比較されます。 証明書がクライアント資格情報として使用されている場合、既定では、WCF は証明書の共通名と拇印をセミコロンで連結し、クライアントのプライマリ id に一意の値を作成します。 `UseAspNetRoles` をサービスの `PrincipalPermissionMode` として設定している場合、このプライマリ ID の値と `Name` プロパティの値を比較してユーザーのアクセス権が決定されます。  
  
     また、自己ホスト型サービスを作成する場合は、次のコードに示すように、コードの <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> プロパティを設定します。  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [サービス操作へのアクセスの承認](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [セキュリティの概要](../../../docs/framework/wcf/feature-details/security-overview.md)
- [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)
