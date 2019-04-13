---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: b0a621da43402777cc620f1876bd968a72bb8c12
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107654"
---
# <a name="reliablesessionbindingelement"></a>ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ReliableSessionBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ReliableSessionBindingElement クラスには、次のプロパティがあります。  
  
### <a name="acknowledgementinterval"></a>AcknowledgementInterval  
 データ型 : datetime  
  
 アクセスの種類:読み取り専用  
  
 ファクトリによって作成された信頼できるチャネルで、メッセージの送信元に受信確認を送信するまで送信先が待機する時間  
  
### <a name="flowcontrolenabled"></a>FlowControlEnabled  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 フロー制御を有効にするかどうかを示すブール値  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 データ型 : datetime  
  
 アクセスの種類:読み取り専用  
  
 他の通信相手がチャネルにメッセージを送信せずにいられる最長期間を指定します。他の通信相手がメッセージを送信しない期間がこの値を超えると、チャネルでエラーが発生します。  
  
### <a name="maxpendingchannels"></a>MaxPendingChannels  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 リスナーで受け入れを待機できるチャネルの最大数。  
  
### <a name="maxretrycount"></a>MaxRetryCount  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 基になるチャネルで `Send` を呼び出すことで、信頼できるチャネルが受信確認を受信していないメッセージの再転送を試みる最大回数  
  
### <a name="maxtransferwindowsize"></a>MaxTransferWindowSize  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 信頼できるセッションの転送ウィンドウの最大サイズ  
  
### <a name="ordered"></a>順序あり  
 データ型 : boolean  
  
 アクセスの種類:読み取り専用  
  
 メッセージが送信された順序で到着されることを保証するかどうかを指定するブール値です。  
  
### <a name="reliablemessagingversion"></a>ReliableMessagingVersion  
 データ型 : integer  
  
 アクセスの種類:読み取り専用  
  
 信頼できるセッションで使用される WS-ReliableMessaging プロトコルのバージョンを指定する整数。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
