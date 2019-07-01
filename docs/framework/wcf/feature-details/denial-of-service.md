---
title: サービス拒否
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: 0946e123e10fbad7357c9be356287e5e87b271d2
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486937"
---
# <a name="denial-of-service"></a>サービス拒否
サービス拒否は、メッセージを処理できなくしたり、メッセージ処理を大幅に遅延させたりするなど、システムに過大な負荷が生じた場合に発生します。  
  
## <a name="excess-memory-consumption"></a>過度のメモリ消費  
 一意のローカル名、名前空間、またはプレフィックスを大量に含んだ XML ドキュメントを読み込むと、問題が発生する場合があります。 <xref:System.Xml.XmlReader> から派生したクラスを使用している場合、<xref:System.Xml.XmlReader.LocalName%2A>、<xref:System.Xml.XmlReader.Prefix%2A>、または <xref:System.Xml.XmlReader.NamespaceURI%2A> のいずれかのプロパティが項目ごとに呼び出され、それによって返された文字列が <xref:System.Xml.NameTable> に追加されます。 <xref:System.Xml.NameTable> が保持するコレクションのサイズは決して減ることがありません。その結果、文字列ハンドルの実質的な "メモリ リーク" が発生する場合があります。  
  
 回避事項を次に示します。  
  
- <xref:System.Xml.NameTable> からの派生クラスを作成し、最大サイズのクォータを指定します (<xref:System.Xml.NameTable> の使用を回避したり、サイズが上限に達したときに <xref:System.Xml.NameTable> を切り替えたりすることはできません)。  
  
- 可能であれば、前述のプロパティを使用せずに、<xref:System.Xml.XmlReader.MoveToAttribute%2A> メソッドと <xref:System.Xml.XmlReader.IsStartElement%2A> メソッドを使用します。これらのメソッドでは、文字列が返されないため、<xref:System.Xml.NameTable> コレクションがあふれてしまう問題を回避できます。  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>悪質なクライアントにより過度のライセンス要求がサービスに送信される  
 悪質なクライアントが過度のライセンス要求を実行してサービスを攻撃する場合、サーバーは過度のメモリを使用することになります。  
  
 軽減策:次のプロパティを使用して、<xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>クラス。  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A> : `SecurityContextToken` または `SPNego` ネゴシエーションの後にサーバーがキャッシュする、期限付きの `SSL` の最大数を制御します。  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A> : `SecurityContextTokens` または `SPNego` ネゴシエーションに続いてサーバーが発行する `SSL` の有効期限を制御します。 サーバーは、この期間の `SecurityContextToken` をキャッシュします。  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: サーバーで確立されているが、そのアプリケーション メッセージが処理されていない、セキュリティで保護されたメッセージ交換の最大数を制御します。 このクォータは、クライアントが、セキュリティで保護されたメッセージ交換をサービスで確立しないようにします。それによって、サービスはクライアントごとの状態を保持できますが、それらの状態を使用することはありません。  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A> : サービスが、セキュリティで保護されたメッセージ交換を、その当事者のクライアントからのアプリケーション メッセージを受信しなくても確立したままにする最長時間を制御します。 このクォータは、クライアントが、セキュリティで保護されたメッセージ交換をサービスで確立しないようにします。それによって、サービスはクライアントごとの状態を保持できますが、それらの状態を使用することはありません。  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding または二重カスタム バインディングにクライアント認証が必要になる  
 既定では、<xref:System.ServiceModel.WSDualHttpBinding> のセキュリティは有効になっています。 ただし、<xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> プロパティを <xref:System.ServiceModel.MessageCredentialType.None> に設定してクライアント認証を無効にすると、第 3 のサービスで悪質なユーザーからサービス拒否攻撃を受ける可能性があります。 これは、悪質なクライアントが、メッセージ ストリームを第 3 のサービスに送信するようサービスに指示できるためです。  
  
 これを防ぐには、このプロパティを `None` に設定しないようにします。 二重メッセージ パターンを持つカスタム バインディングを作成する場合もこの可能性があることに注意してください。  
  
## <a name="auditing-event-log-can-be-filled"></a>監査イベント ログがいっぱいになる可能性がある  
 悪意のあるユーザーに監査が有効になっていることを知られると、その攻撃者に監査エントリの書き込みにつながる無効なメッセージを送信される可能性があります。 このような方法で監査ログに書き込みが行われると、監査システムに障害が発生します。  
  
 これを防ぐには、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> プロパティを `true` に設定し、イベント ビューアーのプロパティを使用して監査動作を制御します。 イベント ビューアーを使用して、イベント ログを表示および管理の詳細については、次を参照してください。[イベント ビューアー](https://go.microsoft.com/fwlink/?LinkId=186123)します。 詳細については、次を参照してください。[監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)します。  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-to-become-unresponsive"></a>サービスが応答しなくなる可能性が IAuthorizationPolicy の無効な実装  
 呼び出す、<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A>の欠陥のある実装のメソッド、<xref:System.IdentityModel.Policy.IAuthorizationPolicy>インターフェイスは、サービスが応答しなくなる可能性で入力する必要があります。  
  
 軽減策:信頼されたコードだけを使用します。 つまり、ユーザーが記述しテストしたコード、または信頼されたプロバイダーが提供するコードのみを使用します。 十分な検討を行わずに、<xref:System.IdentityModel.Policy.IAuthorizationPolicy> の信頼されない拡張をユーザーのコードに接続することを許可しないでください。 これは、サービスの実装で使用されるすべての拡張に当てはまります。 WCF 機能拡張ポイントを使用してアプリケーション コードと接続されている外部コードの違いを行いません。  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Kerberos の最大トークン サイズの変更が必要になる場合がある  
 クライアントが多数のグループ (実際の数はグループにより異なるが、約 900) に属している場合、メッセージ ヘッダーのブロックが 64 KB を超えると問題が発生する場合があります。 Microsoft サポート記事で説明、最大 Kerberos トークン サイズを増やすことができる場合、"[Internet Explorer Kerberos 認証は IIS に接続する十分なバッファーのため機能しません](https://go.microsoft.com/fwlink/?LinkId=89176)"。 また、Kerberos トークンの増加に対応するために WCF メッセージの最大サイズを増やす必要があります。  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>自動登録によってコンピューターに同一サブジェクト名の証明書が複数発生する  
 *自動登録*の機能は、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]ユーザーとコンピューターの証明書を自動的に登録します。 この機能が有効になっているドメイン上にコンピューターがある場合、新しいコンピューターがネットワークに参加するたびに、クライアント認証を目的とする X.509 証明書が自動的に作成されローカル コンピューターの個人用証明書のストアに自動で挿入されます。 ただし、自動登録では、キャッシュに作成されたすべての証明書に同じサブジェクト名が使用されます。  
  
 影響は、自動登録のドメインで開くには WCF サービスが失敗することです。 コンピューターの完全修飾ドメイン ネーム システム (DNS) 名を持つ証明書が複数あるため、既定サービスの X.509 資格情報検索の条件が不明確になり、このような問題が発生します。 この場合、1 つは自動登録で作成された証明書、もう 1 つは自己発行された証明書です。  
  
 これを防ぐに参照をより正確な検索条件を使用して使用する正確な証明書、 [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)します。 たとえば、<xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> オプションを使用し、一意の拇印 (ハッシュ) により証明書を指定します。  
  
 自動登録機能の詳細については、次を参照してください。 [Certificate Autoenrollment in Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=95166)します。  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>複数の代替サブジェクト名の最後が承認に使用される  
 まれなケースとして X.509 証明書に複数の代替サブジェクト名が含まれる場合、その代替サブジェクト名を使用して承認を行うと、承認は失敗する場合があります。  
  
## <a name="protect-configuration-files-with-acls"></a>ACL を使用して構成ファイルを保護する  
 必須およびオプションのクレームは、CardSpace 発行済みトークンのコードと構成ファイルで指定できます。 これにより、対応する要素が、セキュリティ トークン サービスに送信される `RequestSecurityToken` メッセージに送出されます。 攻撃者は、コードまたは構成を変更して必須またはオプションのクレームを削除でき、対象サービスへのアクセスが許可されていないトークンをセキュリティ トークン サービスに発行させることができます。  
  
 : を軽減するには構成ファイルを変更するコンピューターへのアクセスが必要です。 アクセス制御リスト (ACL: Access Control List) を使用して構成ファイルをセキュリティで保護します。 WCF では、コードは、構成から読み込まれるには、このようなコードを許可することは前に、アプリケーション ディレクトリまたはグローバル アセンブリ キャッシュにする必要があります。 ディレクトリの ACL を使用してディレクトリをセキュリティで保護します。  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>1 つのサービスに対して、セキュリティで保護されたセッションが最大数に達する  
 クライアントがサービスにより正常に認証され、セキュリティで保護されたセッションがサービスと共に確立されると、クライアントがセッションをキャンセルするか、セッションの期限が切れるまで、サービスはそのセッションを追跡します。 セッションが確立されるたびに、1 つのサービスで同時にアクティブにできるセッションは上限に近づいていきます。 この上限に達した場合、1 つ以上のアクティブなセッションが期限切れになるかまたはクライアントによりキャンセルされるまで、そのサービスで新しいセッションの作成を試みるクライアントは拒否されます。 クライアントは 1 つのサービスで複数のセッションを保持できますが、その各セッションは上限に反映されます。  
  
> [!NOTE]
>  ステートフルなセッションを使用する場合、前の段落は適用されません。 ステートフルなセッションの詳細については、次を参照してください。[方法。セキュリティ コンテキストを作成、セキュリティで保護されたセッションのトークン](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)します。  
  
 これを防ぐには、<xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの <xref:System.ServiceModel.Channels.SecurityBindingElement> プロパティを設定して、アクティブなセッションの最大数とセッションの最長有効期間の制限を設定します。  
  
## <a name="see-also"></a>関連項目

- [セキュリティの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [情報の漏えい](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [権限の昇格](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [サービス拒否](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [改変](../../../../docs/framework/wcf/feature-details/tampering.md)
- [サポートされていないシナリオ:](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
