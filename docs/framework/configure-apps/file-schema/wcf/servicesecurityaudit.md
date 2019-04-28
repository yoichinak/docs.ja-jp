---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 384a1cdb6d39f4d6ecd2353a15c0da7c6d2e82bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758120"
---
# <a name="servicesecurityaudit"></a>\<serviceSecurityAudit>
サービス操作中にセキュリティ イベントの監査を有効にする設定を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceSecurityAudit>  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|auditLogLocation|監査ログの場所を指定します。 以下の値が有効です。<br /><br /> -既定値:セキュリティ イベントがログに書き込まれます、アプリケーションで Windows XP、およびイベント ログに Windows Server 2003 および Windows Vista で。<br />アプリケーション:監査イベントは、アプリケーション イベント ログに書き込まれます。<br />セキュリティ:監査イベントには、セキュリティ イベント ログには書き込まれます。<br /><br /> 既定値は Default です。 詳細については、「 <xref:System.ServiceModel.AuditLogLocation> 」を参照してください。|  
|suppressAuditFailure|監査ログへの書き込みエラーを非表示にする動作を指定します。<br /><br /> アプリケーションには、監査ログへの書き込みエラーを通知する必要があります。 アプリケーションが監査エラーを処理するように設計されていない場合は、この属性を使用して、監査ログへの書き込みでのエラーが表示されないようにする必要があります。<br /><br /> この属性が `true` の場合、監査イベントの書き込み試行の結果発生する例外 (ただし、OutOfMemoryException、StackOverFlowException、ThreadAbortException、および ArgumentException を除く) はシステムによって処理され、アプリケーションには伝達されません。 この属性が `false` の場合、監査イベントの書き込み試行の結果発生する例外は、すべてアプリケーションまで渡されます。<br /><br /> 既定値は `true` です。|  
|serviceAuthorizationAuditLevel|監査ログに記録される承認イベントの種類を指定します。 以下の値が有効です。<br /><br /> -None。サービス承認イベントの監査は実行されません。<br />-成功:成功したサービス承認イベントだけが監査されます。<br />-エラー:失敗したサービス承認イベントだけが監査されます。<br />-SuccessOrFailure:サービス承認イベントの成功と失敗の両方が監査されます。<br /><br /> 既定値は None です。 詳細については、「 <xref:System.ServiceModel.AuditLevel> 」を参照してください。|  
|messageAuthenticationAuditLevel|ログに記録されるメッセージ認証監査イベントの種類を指定します。 以下の値が有効です。<br /><br /> -None。監査イベントは生成されません。<br />-成功:成功したセキュリティ (メッセージ署名の検証、暗号、およびトークンの検証を含む完全な検証) イベントのみが記録されます。<br />-エラー:失敗したイベントだけが記録されます。<br />-SuccessOrFailure:成功と失敗の両方のイベントが記録されます。<br /><br /> 既定値は None です。 詳細については、「 <xref:System.ServiceModel.AuditLevel> 」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## <a name="remarks"></a>Remarks  
 この構成要素を使用して、Windows Communication Foundation (WCF) 認証イベントを監査します。 監査を有効にすると、成功した認証、失敗した認証、またはその両方を監査できます。 イベントは、3 種類のイベント ログ (アプリケーション ログ、セキュリティ ログ、およびオペレーティング システムのバージョンに対する既定のログ) のいずれかに書き込まれます。 イベント ログはすべて、Windows イベント ビューアーを使用して表示できます。  
  
 この構成要素の使い方の詳細な例を参照してください。[サービス監査動作](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)します。  
  
 監査イベントは既定で、Windows XP の場合はアプリケーション ログに、Windows Server 2003 と Windows Vista の場合はセキュリティ ログに表示されます。 監査イベントの場所は、`auditLogLocation` 属性を "Application" または "Security" に設定することによって指定できます。 詳細については、「[方法 :セキュリティ イベントを監査](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)します。 書き込むオブジェクトへのアクセスを有効にする]-> [場合は、イベントは、セキュリティ ログに書き込まれますが、「成功」と「エラー」に設定する必要があります。  
  
 イベント ログを調べる場合、監査イベントのソースは "ServiceModel Audit 3.0.0.0" です。 メッセージ認証監査レコードには "MessageAuthentication" のカテゴリ、サービス承認監査レコードには "ServiceAuthorization" のカテゴリが設定されます。  
  
 メッセージ認証監査イベントは、メッセージの改ざんや期限切れの有無、クライアントによるサービス認証の成否などに適用されます。 このイベントでは、認証の成功または失敗に関する情報とクライアント ID、およびメッセージ送信先のエンドポイントとそのメッセージに関連付けられたアクションに関する情報が提供されます。  
  
 サービス承認監査イベントは、サービス承認マネージャーによって決定される承認に適用されます。 承認が成功するかどうかに関する情報が提供または失敗すると、クライアントの id と共に、メッセージ送信先のエンドポイントから生成された承認コンテキストの識別子、メッセージに関連付けられたアクションを受信メッセージおよびアクセス決定を行った承認マネージャーの種類。  
  
## <a name="example"></a>例  
  
```xml  
<system.serviceModel>
  <behaviors>
    <serviceBehaviors>
      <behavior name="NewBehavior">
        <serviceSecurityAudit auditLogLocation="Application"
                              suppressAuditFailure="true"
                              serviceAuthorizationAuditLevel="Success"
                              messageAuthenticationAuditLevel="Success" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [監査](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [方法: セキュリティ イベントを監査します。](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [サービス監査動作](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
