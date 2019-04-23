---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ba9031dad96f12c7c48b03f1da4af1b3adc6dd4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980436"
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>メソッド  
 PeerTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 PeerTransportBindingElement クラスには、次のプロパティがあります。  
  
### <a name="listenipaddress"></a>ListenIPAddress  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 ピア ノードがメッセージをリッスンする IP アドレスです。  
  
### <a name="port"></a>ポート  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 このバインディングがピア チャネル メッセージを処理するネットワーク インターフェイス ポートです。  
  
### <a name="security"></a>セキュリティ  
 データの種類:PeerSecuritySettings  
  
 アクセスの種類:読み取り専用  
  
 ピア トランスポートのセキュリティ設定です。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
