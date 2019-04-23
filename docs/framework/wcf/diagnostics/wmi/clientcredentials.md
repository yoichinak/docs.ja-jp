---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c3adc675bb6c1e9011459a88fd7dc8e8cf63a880
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771206"
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>構文  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ClientCredentials クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ClientCredentials クラスには、次のプロパティがあります。  
  
### <a name="clientcertificate"></a>ClientCertificate  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 クライアントがサービスに対して自身を認証するために使用する X.509 証明書です。  
  
### <a name="httpdigest"></a>HttpDigest  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 現在の Http ダイジェスト資格情報です。  
  
### <a name="issuedtoken"></a>IssuedToken  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 ローカル セキュリティ トークン サービスにアクセスするために使用されるエンドポイント アドレスおよびバインディングです。  
  
### <a name="peer"></a>Peer  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 ピア ノードがメッシュ内の他のノードに対して自身を認証するために使用する資格情報です。  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 サービスの X.509 証明書です。  
  
### <a name="supportinteractive"></a>SupportInteractive  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 資格情報が対話的なネゴシエーションをサポートしているかどうかを指定するブール値です。  
  
### <a name="username"></a>UserName  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 クライアントがサービスに対して自身を認証するために使用するユーザー名とパスワードです。  
  
### <a name="windows"></a>Windows  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 クライアントがサービスに対して自身を認証するために使用する Windows 資格情報です。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ClientCredentials>
