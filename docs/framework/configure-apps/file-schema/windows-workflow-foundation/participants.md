---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: ffb38bca1848d7f679b6a2a717cd7082cfe356f3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360347"
---
# <a name="participants"></a>\<参加者 >
ランタイムから直接出力される追跡レコードをリッスンし、追跡レコードの構成方法に従って処理を行う追跡参加要素の一覧を構成します。 これには、特定の出力 (ファイル、コンソール、ETW など) への書き込み、レコードの処理や集計、またはその他の必要な組み合わせが含まれます。  
  
 ワークフロー追跡と追跡参加要素の詳細については、次を参照してください。[ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)と[追跡参加要素](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)します。  
  
\<system.serviceModel>  
\<追跡 >  
\<参加者 >  
  
## <a name="syntax"></a>構文  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|追跡参加要素を処理するための設定が含まれます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<tracking>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|ワークフロー サービスの追跡設定を定義する構成セクションを表します。|  
  
## <a name="remarks"></a>Remarks  
 追跡参加要素は、ワークフローから生成される追跡データを取得し、それを別のメディアに保存するために使用します。 同様に、追跡レコードの後処理はすべて、追跡参加要素内でも実行できます。  
  
 複数の追跡参加要素が追跡イベントを同時に使用することができます。 各追跡参加要素は、それぞれ別の追跡プロファイルと関連付けることができます。  
  
 追跡レコードを ETW セッションに書き込む、標準の追跡参加要素が用意されています。 参加要素は、追跡固有の動作を構成ファイルに追加することによって、ワークフロー サービスで構成されます。 ETW 追跡参加要素を有効にすると、追跡レコードをイベント ビューアーで表示できます。 これで要件が満たされない場合は、カスタムの追跡参加要素を作成することもできます。  
  
## <a name="example"></a>例  
 次の構成例は、Web.config ファイルで構成されている標準の ETW 追跡参加要素を示します。  
  
 ETW 追跡参加要素が追跡レコードを ETW に書き込むために使用するプロバイダー Id が定義されている、 **\<診断 >** セクション。 追跡参加要素には、その要素が定期受信した追跡レコードを指定するためのプロファイルが関連付けられています。 これは、 **profileName**の属性、 **\<追加 >** 要素。 これらが定義に追跡参加要素が追加、  **\<etwTracking >** サービス動作。 これにより、選択した追跡参加要素がワークフロー インスタンスの拡張機能に追加され、追跡レコードの受信が開始されます。  
  
```xml
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [ワークフローの追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追跡参加要素](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
