---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230929"
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>構文  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceCredentials クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 ServiceCredentials クラスには、次のプロパティがあります。  
  
### <a name="clientcertificate"></a>ClientCertificate  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 このサービスのための、クライアント証明認証および提供設定です。  
  
### <a name="issuedtokenauthentication"></a>IssuedTokenAuthentication  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 このサービスのための、現在発行されているトークンの認証設定です。  
  
### <a name="peer"></a>Peer  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 ピアのトランスポート エンドポイントによって使用される、現在の証明書の認証および提供の設定です。  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 現在のセキュリティで保護された通信の設定を指定します。  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 このサービスに関連付けられている証明書です。  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 このサービスのユーザー名/パスワードの設定です。  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 このサービスの Windows 認証の設定です。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ServiceCredentials>
