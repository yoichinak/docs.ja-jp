---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: b65cc4d04b5304e93b70509c9db3bc2248accb7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926437"
---
# <a name="backuplists"></a>\<backupLists >
エラー処理に使用されるバックアップ サービス セットを定義する構成セクションを表します。 各子要素は、プライマリエンドポイントに到達できない場合にルーティングサービスによって使用される一連のエンドポイントを列挙するバックアップリストです。 リストの最初のエンドポイントがダウンしていると、ルーティング サービスは自動的にリスト内で次にあるエンドポイントにフェールオーバーします。  これにより、クライアント アプリケーションに複雑なパターンの処理方法やサービスの配置場所を示すことなく、アプリケーションの信頼性を高めることができます。  
  
 \<system.serviceModel>  
\<ルーティング >  
\<backupLists >  
  
## <a name="syntax"></a>構文  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filter>](filter.md)|プライマリエンドポイントに到達できない場合に、ルーティングサービスで使用するエンドポイントの一覧が含まれています。 .|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ルーティング >](routing.md)|一連のルーティングフィルターを定義するための構成セクションを表します。これにより、受信メッセージ<xref:System.ServiceModel.Dispatcher.MessageFilter>を評価するときに使用する Windows Communication Foundation (WCF) の種類、およびターゲットエンドポイントを定義するルーティングテーブルを決定します。フィルターが一致したときにメッセージをに送信します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
