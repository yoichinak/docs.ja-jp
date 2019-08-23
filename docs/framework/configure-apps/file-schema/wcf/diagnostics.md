---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 170cae5b328c86073c1d8e7710bb19e98ab5688c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925873"
---
# <a name="diagnostics"></a>\<診断 >
`diagnostics` 要素は、ランタイムの検査と管理を行う管理者が使用できる設定を定義します。  
  
 \<system.ServiceModel >  
\<診断 >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|etwProviderId|イベントを ETW セッションに書き込むイベント追跡プロバイダーの識別子を指定する文字列。|  
|performanceCounters|アセンブリのパフォーマンス カウンターが有効であるかどうかを指定します。 有効な値は、次のとおりです。<br /><br /> オートパフォーマンス カウンターは無効です。<br />ServiceOnlyこのサービスに関連するパフォーマンス カウンターだけが有効です。<br />なパフォーマンス カウンターは実行時に表示できます。<br />標準単一のパフォーマンス カウンター インスタンス _WCF_Admin が作成されます。 このインスタンスは、インフラストラクチャで使用される SQM データのコレクションを有効にするために使用されます。 このインスタンスのカウンター値は更新されず、0 のままになります。 WCF の構成が存在しない場合は、これが既定値になります。|  
|wmiProviderEnabled|アセンブリの WMI プロバイダーが有効であるかどうかを指定するブール値。 ユーザーが Windows Communication Foundation (WCF) の検査および制御機能に対する実行時アクセス権を取得するには、WMI プロバイダーが必要です。 既定値は `false` です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<endToEndTracing >](endtoendtracing.md)|サービス アプリケーションの実行中にエンドツーエンドのトレースのさまざまな側面を有効または無効にするための構成要素。|  
|[\<messageLogging >](messagelogging.md)|WCF メッセージ ログの設定について説明します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|serviceModel|すべての WCF 構成要素のルート要素です。|  
  
## <a name="remarks"></a>Remarks  
 `diagnostics` セクションは、アセンブリに配置されるすべてのサービスの診断設定を定義します。 アセンブリ内のサービスが 1 つでない限り、サービス レベル別に診断設定を定義することはできません。 属性は、セクションの要件に応じて設定されます。  
  
## <a name="example"></a>例  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
                  logMalformedMessages="true"
                  logMessagesAtServiceLevel="true"
                  logMessagesAtTransportLevel="true"
                  maxMessagesToLog="42"
                  maxSizeOfMessageToLog="42">
    <filters>
      <clear />
    </filters>
  </messageLogging>
</diagnostics>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
