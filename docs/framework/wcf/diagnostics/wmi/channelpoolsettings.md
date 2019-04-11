---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 8900af77d0d385bb68b4b85e1d15be57bb7a8d14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131912"
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings
ChannelPoolSettings  
  
## <a name="syntax"></a>構文  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ChannelPoolSettings クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ChannelPoolSettings クラスには、次のプロパティがあります。  
  
### <a name="idletimeout"></a>IdleTimeout  
 データ型 : datetime  
  
 アクセスの種類:読み取り専用  
  
 接続が切断されるまでの最大アイドル時間。  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 データ型 : datetime  
  
 アクセスの種類:読み取り専用  
  
 リース操作の完了がタイムアウトするまでの最大時間。  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 各エンドポイントでの送信チャネルの最大数。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
