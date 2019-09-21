---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399540"
---
# <a name="soapprocessing"></a>\<soapProcessing >

異なるバインディングの種類およびメッセージ バージョンの間でメッセージのマーシャリングに使用されるクライアント エンドポイントの動作を定義します。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<動作 >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<動作 >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<soapProcessing >**
  
## <a name="syntax"></a>構文  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
  
以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|                   | 説明 |
| ----------------- | ----------- |
| `processMessages` | SOAP メッセージ バージョン間のメッセージをマーシャリングするかどうかを指定するブール値。 |

### <a name="child-elements"></a>子要素

なし

### <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| [ **\<動作 >** ](behavior-of-endpointbehaviors.md) | エンドポイントの動作を指定します。 |

## <a name="remarks"></a>Remarks

SOAP 処理は、メッセージ バージョン間でメッセージが変換されるプロセスです。

Windows Communication Foundation (WCF) ルーティングサービスでは、あるプロトコルから別のプロトコルにメッセージを変換できます。 受信メッセージのバージョンと送信メッセージのバージョンが異なる場合、新しいメッセージが正しいバージョンで作成されます。 受信 WCF メッセージの本文および関連するヘッダーが含まれた新しい WCF メッセージを作成することで、ある <xref:System.ServiceModel.Channels.MessageVersion> から別のメッセージ バージョンへのメッセージの変換が完了します。 アドレス指定に固有のヘッダーまたはルーター レベルで認識されるヘッダーは、新しい WCF メッセージの作成に使用されません。これらのヘッダーは、異なるバージョンであるか (アドレス指定ヘッダーの場合)、クライアントとルーターの間の通信の一部として処理されているためです。

発信メッセージにヘッダーが配置されるかどうかは、受信チャネル層を介して渡されたと認識されるようにマークされているかどうかによって決まります。 認識されないヘッダー (カスタム ヘッダーなど) は削除されずに送信メッセージにコピーされ、ルーティング サービスを介して渡されます。 メッセージの本文は、送信メッセージにコピーされます。 そして、メッセージは送信チャネルに送信されます。この時点で、すべてのヘッダー、および使用されている通信プロトコル/トランスポートに固有のエンベロープ データが作成され、追加されます。

このような処理手順は、SOAP 処理動作が指定されているときに行われます。 [この\<soapprocessingextension >](soapprocessing.md)動作は、ルーティングサービスの開始時にすべてのクライアント (送信) エンドポイントに適用されるエンドポイントの動作です。 既定では、 [ \<ルーティング >](routing-of-servicebehavior.md)動作は、クライアントエンドポイントごとにをに`true`設定`processMessages`して、新しい[ \<soapprocessingextension >](soapprocessing.md)動作を作成してアタッチします。 ルーティング サービスが認識しないプロトコルを使用している場合や既定の処理動作をオーバーライドする場合は、ルーティング サービス全体または特定のエンドポイントにおいて SOAP 処理を無効にできます。  すべてのエンドポイントのルーティングサービス全体で SOAP 処理を無効にする`soapProcessing`には、 [ \<ルーティング >](routing-of-servicebehavior.md)動作の`false`属性をに設定します。 特定のエンドポイントで SOAP 処理を無効にするには、この動作を使用して `processMessages` 属性を `false` に設定してから、既定の処理コードを実行しないエンドポイントにこの動作をアタッチします。  [ \<ルーティング >](routing-of-servicebehavior.md)の動作がルーティングサービスを設定すると、既に存在しているため、エンドポイントの動作の再適用はスキップされます。
