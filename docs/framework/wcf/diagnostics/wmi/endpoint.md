---
title: エンドポイント
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 03c401358839671d750985b95b1aada599931aad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795898"
---
# <a name="endpoint"></a>エンドポイント
エンドポイント  
  
## <a name="syntax"></a>構文  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a>メソッド  
 Endpoint クラスは次のメソッドを定義します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](getoperationcounterinstancename.md)|操作パフォーマンス カウンターのインスタンスの名前を取得します。|  
  
## <a name="properties"></a>プロパティ  
 Endpoint クラスには次のプロパティがあります。  
  
### <a name="address"></a>Address  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 エンドポイントのアドレスを格納している URI。  
  
### <a name="addressheaders"></a>AddressHeaders  
 データ型 : string array  
  
 アクセスの種類:読み取り専用です。  
  
 このエンドポイントに接続しているアドレス ヘッダーのコレクション  
  
### <a name="addressidentity"></a>AddressIdentity  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 エンドポイントの ID  
  
### <a name="appdomainid"></a>AppDomainId  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用です。  
  
 エンドポイントをホストする appdomain の appdomain ID  
  
### <a name="behaviors"></a>ビヘイビアー  
 データの種類:動作の配列  
  
 アクセスの種類:読み取り専用です。  
  
 このエンドポイントが実装する動作のコレクション  
  
### <a name="binding"></a>バインディング  
 データの種類:バインディング  
  
 アクセスの種類:読み取り専用です。  
  
 このエンドポイントが使用するバインディング  
  
### <a name="contractname"></a>ContractName  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 このエンドポイントが公開するコントラクトを指定する文字列  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 エンドポイントのパフォーマンス カウンターのインスタンス名  
  
### <a name="listenuri"></a>ListenUri  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 エンドポイントがリッスンする URI  
  
### <a name="name"></a>Name  
 データ型: string  
  
 アクセスの種類:読み取り専用です。  
  
 このエンドポイントの一意の名前  
  
### <a name="processid"></a>ProcessId  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用です。  
  
 エンドポイントをホストするプロセスのプロセス ID  
  
### <a name="ref"></a>ref  
 データの種類:コントラクト  
  
 アクセスの種類:読み取り専用です。  
  
 このエンドポイントが公開しているコントラクト。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|
