---
title: '方法: 信頼できるセッション内でメッセージをセキュリティ保護します。'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: ee35f2a36ca08814423b5a3d0b1432bacd28c2e5
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/16/2019
ms.locfileid: "56333054"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>方法: 信頼できるセッション内でメッセージをセキュリティ保護します。

ここでは、信頼できるセッション内で交換されるメッセージに対して、メッセージ レベルのセキュリティを有効にするために必要な手順について説明します。このとき、信頼できるセッションがオプションでサポートされているシステム指定のバインディングを使用します。 コードを使用して強制的に行う、または構成ファイルで宣言によって、セキュリティで保護された、信頼できるセッションを有効にします。 この手順では、クライアントとサービスの構成ファイルを使用して、セキュリティで保護された信頼できるセッションを有効にします。

この手順の主な部分は、次の 3 つのタスクで構成されます。

1. クライアントとサービスのメッセージ交換は信頼できるセッション内で行うことを指定します。

1. 信頼できるセッション内でメッセージ レベルのセキュリティを要求します。

1. サービスに対する認証時にクライアントが使用する必要があるクライアント資格情報を指定します。

エンドポイントの構成要素が含まれている最初のタスクで重要ですが、 `bindingConfiguration` (この例では) でという名前のバインド構成を参照する属性`MessageSecurity`。 [ **\<バインド >** ](../../../../docs/framework/misc/binding.md)構成要素を設定して、信頼できるセッションを有効にするには、この名前を参照し、`enabled`の属性、 [  **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))要素`true`します。 信頼できるセッション内で使用できる順序付き配信の保証は、`ordered` 属性を `true` に設定することによって要求できます。

この構成手順は、基になる例のソースのコピーを、 [WS 信頼できるセッション](../../../../docs/framework/wcf/samples/ws-reliable-session.md)を参照してください。

2 番目のタスクの必要な項目は、設定によって実現されます、`mode`の属性、 **\<セキュリティ >** 要素に含まれている、 **\<バインド >** 要素は、クライアントとサービスの`Message`します。

3 番目のタスクの必要な項目は、設定によって実現されます、`clientCredentialType`の属性、 **\<メッセージ >** 要素に含まれている、 **\<セキュリティ >** 要素は、クライアントとサービスの`Certificate`します。

> [!NOTE]
> メッセージ セキュリティを使用して、信頼できるセッションで、最初のエラーと例外をスローする代わりにタイムアウトが発生するまでに、認証されていないクライアントを認証すると信頼性の高いメッセージングされます。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用する WSHttpBinding 使用サービスを構成します。

この手順で説明されて[方法。信頼できるセッション内でメッセージを交換](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)します。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用して、WSHttpBinding でクライアントを構成します。

この手順で説明されて[方法。信頼できるセッション内でメッセージを交換](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)します。

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>構成でモードと ClientCredentialType を設定します。

1. 適切なバインド要素を追加、 [ **\<バインド >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)構成ファイルの要素。 次の例では、追加、 [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)要素。

1. 追加、 **\<バインド >** 要素とその`name`属性に適切な値。 例では、名前を使用して`MessageSecurity`します。

1. 追加、 **\<セキュリティ >** 要素、`mode`属性を`Message`します。

1. 内で、 **\<セキュリティ >** 要素を追加、 **\<メッセージ >** 要素、`clientCredentialType`属性を`Certificate`します。

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
