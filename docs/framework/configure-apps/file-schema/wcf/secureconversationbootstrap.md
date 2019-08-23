---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: 2ee9a715929641abc605a31ac00fb154b863cc8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935847"
---
# <a name="secureconversationbootstrap"></a>\<secureConversationBootstrap>
セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<セキュリティ >  
\<secureConversationBootstrap>  
  
## <a name="syntax"></a>構文  
  
```xml  
<secureConversationBootstrap allowSerializedSigningTokenOnReply="Boolean"
                             authenticationMode="AuthenticationMode"
                             defaultAlgorithmSuite="SecurityAlgorithmSuite"
                             includeTimestamp="Boolean"
                             requireDerivedKeys="Boolean"
                             keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
                             messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
                             messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
                             requireDerivedKeys="Boolean"
                             requireSecurityContextCancellation="Boolean"
                             requireSignatureConfirmation="Boolean"
                             securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
                             includeTimestamp="Boolean" />
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|任意。 シリアル化されたトークンを応答で使用できる場合に指定するブール値。 既定値は `false` です。 二重バインドを使用する場合、この設定の既定値は `true` に設定され、行った設定はすべて無視されます。|  
|`authenticationMode`|イニシエーターとレスポンダーの間で使用される SOAP 認証モードを指定します。<br /><br /> 既定値は sspiNegotiated です。<br /><br /> この属性は <xref:System.ServiceModel.Configuration.AuthenticationMode> 型です。|  
|`defaultAlgorithmSuite`|セキュリティ アルゴリズム スイートは、正規化、ダイジェスト、キーラップ、署名、暗号化、およびキー派生の各アルゴリズムなど、さまざまなアルゴリズムを定義します。 各セキュリティ アルゴリズム スイートは、これらのさまざまなパラメーターの値を定義します。 メッセージ ベースのセキュリティは、これらのアルゴリズムを使用して実現されます。<br /><br /> この属性は、既定とは異なるアルゴリズムのセットを選択する別のプラットフォームで操作するときに使用されます。 この設定を修正する場合、関連するアルゴリズムの強さと脆弱性に注意する必要があります。 この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。 既定値は `Basic256` です。|  
|`includeTimestamp`|各メッセージにタイム スタンプが含まれるかどうかを指定するブール値です。 既定値は `true` です。|  
|`keyEntropyMode`|メッセージをセキュリティで保護するキーを計算する方法を指定します。 キーは、クライアント キー マテリアルのみ、サービス キー マテリアルのみ、または両方の組み合わせに基づいて生成できます。 有効な値は、<br /><br /> -ClientEntropy:セッションキーは、クライアントが提供したキーマテリアルに基づいています。<br />-ServerEntropy:セッションキーは、サービスが提供するキーマテリアルに基づいています。<br />-連結 Edエントロピ:セッションキーは、クライアントとサービスから提供されるキー生成情報に基づいています。<br /><br /> 既定値は CombinedEntropy です。<br /><br /> この属性は <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> 型です。|  
|`messageProtectionOrder`|メッセージ レベルのセキュリティ アルゴリズムをメッセージに適用する順序を設定します。 有効な値は次のとおりです。<br /><br /> SignBeforeEncrypt最初に署名してから、暗号化します。<br />SignBeforeEncryptAndEncryptSignature署名、暗号化、署名を暗号化します。<br />EncryptBeforeSign最初に暗号化し、次に署名します。<br /><br /> SignBeforeEncryptAndEncryptSignature は、WS-Security 1.1 による相互証明書を使用する場合の既定値です。  SignBeforeEncrypt は、WS-Security 1. 0 での既定値です。<br /><br /> この属性は <xref:System.ServiceModel.Security.MessageProtectionOrder> 型です。|  
|`messageSecurityVersion`|使用される WS-Security のバージョンを設定します。 有効な値は次のとおりです。<br /><br /> - WSSecurityJan2004<br />-   WSSecurityXXX2005<br /><br /> 既定値は WSSecurityXXX2005 です。 この属性は <xref:System.ServiceModel.MessageSecurityVersion> 型です。|  
|`requireDerivedKeys`|キーを元の証明キーから派生できるかどうかを指定するブール値。 既定値は `true` です。|  
|`requireSecurityContextCancellation`|セキュリティ コンテキストが不要になったときにそれをキャンセルして終了する必要があるかどうかを指定するブール値。 既定値は `true` です。|  
|`requireSignatureConfirmation`|WS-Security 署名確認を有効にするかどうかを指定するブール値です。 `true` に設定されている場合、メッセージ署名が応答側で確認されます。 既定値は `false` です。<br /><br /> サービスが要求を完全に認識して応答していることを確認するために、署名確認を使用します。|  
|`securityHeaderLayout`|セキュリティ ヘッダーでの要素の順序を指定します。 有効な値は、<br /><br /> 厳密な. "使用前に宣言する" という一般的な方針に従って、項目がセキュリティ ヘッダーに追加されます。<br />緩い. 項目は、WSS: SOAP メッセージ セキュリティに準じた任意の順序でセキュリティ ヘッダーに追加されます。<br />- LaxWithTimestampFirst. 項目は、WSS: SOAP メッセージ セキュリティに準じた任意の順序でセキュリティ ヘッダーに追加されます。ただし、セキュリティ ヘッダー内の最初の要素が wsse:Timestamp 要素でなければならないという点を除きます。<br />- LaxWithTimestampLast. 項目は、WSS: SOAP メッセージ セキュリティに準じた任意の順序でセキュリティ ヘッダーに追加されます。ただし、セキュリティ ヘッダー内の最後の要素が wsse:Timestamp 要素でなければならないという点を除きます。<br /><br /> 既定値は Strict です。<br /><br /> この要素は <xref:System.ServiceModel.Channels.SecurityHeaderLayout> 型です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|現在発行されているトークンを指定します。 この要素は <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement> 型です。|  
|[\<localClientSettings>](localclientsettings-element.md)|このバインディングのローカル クライアントのセキュリティ設定を指定します。 この要素は <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement> 型です。|  
|[\<localServiceSettings>](localservicesettings-element.md)|このバインディングのローカル サービスのセキュリティ設定を指定します。 この要素は <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|カスタム バインドのセキュリティ オプションを指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [バインディング](../../../wcf/bindings.md)
- [バインディングの拡張](../../../wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [方法: 設定を使用してカスタムバインディングを作成する](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [カスタム バインド セキュリティ](../../../wcf/samples/custom-binding-security.md)
