---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 04e6abc5941ec99769ff2c15d47881b60e81d2e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973528"
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ConnectionOrientedTransportBindingElement クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 ConnectionOrientedTransportBindingElement クラスには、次のプロパティがあります。  
  
### <a name="channelinitializationtimeout"></a>ChannelInitializationTimeout  
 データ型 : datetime  
  
 アクセスの種類:読み取り専用  
  
 チャネルの初期化が開始されてからタイムアウトになるまでの時間の長さを示す期間。  
  
### <a name="connectionbuffersize"></a>ConnectionBufferSize  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 クライアントまたサービスからネットワークでシリアル化されたメッセージのチャンクを転送するために使用されるバッファーのサイズ。  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 URI の照合時にサービスに到達するため、ホスト名が使用されたかどうかを示す値。  
  
### <a name="maxbuffersize"></a>MaxBufferSize  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 使用するバッファーの最大サイズ。  
  
### <a name="maxoutputdelay"></a>MaxOutputDelay  
 データ型 : datetime  
  
 アクセスの種類:読み取り専用  
  
 メッセージのチャンクまたは完全なメッセージを、送信前にメモリ内のバッファーに残したままにできる最長期間。  
  
### <a name="maxpendingaccepts"></a>MaxPendingAccepts  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 サービスでの着信接続処理に使用できる保留中の非同期受け入れスレッドの最大数。  
  
### <a name="maxpendingconnections"></a>MaxPendingConnections  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 保留状態の接続の最大数。  
  
### <a name="transfermode"></a>TransferMode  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 接続指向トランスポートを使用して、メッセージをバッファーするかまたはストリームするかを指定する値。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
