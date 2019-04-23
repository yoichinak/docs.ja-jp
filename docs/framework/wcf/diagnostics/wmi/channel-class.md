---
title: チャネル クラス
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767449"
---
# <a name="channel-class"></a>チャネル クラス
チャネル  
  
## <a name="syntax"></a>構文  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>メソッド  
 チャネル クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 チャネル クラスには、次のプロパティがあります。  
  
### <a name="localaddress"></a>LocalAddress  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 チャネルのローカル エンドポイント。  
  
### <a name="ref"></a>ref  
 データの種類:エンドポイント  
  
 アクセスの種類:読み取り専用  
  
 チャネルが接続するエンドポイントへの参照。  
  
### <a name="remoteaddress"></a>RemoteAddress  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 チャネルに関連するリモート アドレス。  
  
### <a name="sessionid"></a>SessionId  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 現在のセッション ID (存在する場合)。  
  
### <a name="type"></a>型  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 チャネルの型。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.ChannelBase>
