---
title: サービス
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991446"
---
# <a name="service"></a>サービス
サービス  
  
## <a name="syntax"></a>構文  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>メソッド  
 Service クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 Service クラスには次のプロパティがあります。  
  
### <a name="baseaddresses"></a>BaseAddresses  
 データ型 : string array  
  
 アクセスの種類:読み取り専用  
  
 サービスによって使用されるベース アドレスです。  
  
### <a name="behaviors"></a>ビヘイビアー  
 データの種類:動作の配列  
  
 アクセスの種類:読み取り専用  
  
 このサービスに関連付けられている動作です。  
  
### <a name="configurationname"></a>ConfigurationName  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 サービスのパフォーマンス カウンターのインスタンスのインスタンス名です。  
  
### <a name="distinguishedname"></a>DistinguishedName  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 アドレスでのサービス名です。  
  
### <a name="extensions"></a>拡張機能  
 データ型 : string array  
  
 アクセスの種類:読み取り専用  
  
 サービス インスタンスの拡張に対するインスタンス コンテキストです。  
  
### <a name="metadata"></a>メタデータ  
 データ型 : string array  
  
 アクセスの種類:読み取り専用  
  
 サービス メタデータの設定です。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 このサービスの一意の名前。  
  
### <a name="namespace"></a>名前空間  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 サービスの名前空間です。  
  
### <a name="opened"></a>Opened  
 データ型 : datetime  
  
 アクセスの種類:読み取り専用  
  
 サービスが開かれた時刻です。  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 データの種類:チャネルの配列  
  
 アクセスの種類:読み取り専用  
  
 サービス インスタンスから送信しているチャネルです。  
  
### <a name="processid"></a>ProcessId  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 サービスをホストするプロセスのプロセス ID です。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|
