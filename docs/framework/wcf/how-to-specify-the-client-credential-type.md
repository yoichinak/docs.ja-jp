---
title: '方法: クライアントの資格情報の種類を指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 775c6a297047c7a0e16db091f9a22686fdb01efb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339399"
---
# <a name="how-to-specify-the-client-credential-type"></a>方法: クライアントの資格情報の種類を指定する
セキュリティ モード (トランスポートまたはメッセージ) を設定してから、クライアント資格情報の種類を指定することができます。 このプロパティでは、クライアントが認証時にサービスに提供する必要のある資格情報の種類を指定します。 セキュリティ モード (クライアントの資格情報の種類を設定する前に必要な手順) を設定する方法についての詳細については、次を参照してください。[方法。セキュリティ モードを設定](../../../docs/framework/wcf/how-to-set-the-security-mode.md)します。  
  
### <a name="to-set-the-client-credential-type-in-code"></a>コードでクライアント資格情報の種類を設定するには  
  
1. サービスで使用されるバインドのインスタンスを作成します。 この例では、<xref:System.ServiceModel.WSHttpBinding> バインドを使用します。  
  
2. <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> プロパティに適切な値を設定します。 この例では、メッセージ モードを使用します。  
  
3. <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> プロパティに適切な値を設定します。 この例では、Windows 認証 (<xref:System.ServiceModel.MessageCredentialType.Windows>) を使用するように設定します。  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>構成でクライアント資格情報の種類を設定するには  
  
1. 追加、 [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素を構成ファイル。  
  
2. 子要素として追加する[\<バインド >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)要素。  
  
3. 適切なバインドを追加します。 この例では、 [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)要素。  
  
4. 追加、 [\<バインド >](../../../docs/framework/misc/binding.md)要素、`name`属性に適切な値。 この例では、"SecureBinding" という名前を使用します。  
  
5. `<security>` バインドを追加します。 `mode` 属性を適切な値に設定します。 この例では、`"Message"` に設定します。  
  
6. セキュリティ モードによって、`<message>` 要素と `<transport>` 要素のどちらかを追加します。 `clientCredentialType` 属性を適切な値に設定します。 この例では `"Windows"` を使用します。  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a>関連項目

- [サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)
- [方法: セキュリティ モードを設定します。](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
