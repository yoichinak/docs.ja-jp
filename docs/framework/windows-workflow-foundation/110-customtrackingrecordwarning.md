---
title: "110 – CustomTrackingRecordWarning"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bc093de-be47-4ed0-983f-05b4246446fc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 340472efc78d6b5fdb336e46ebffc223fe8dfaff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="110---customtrackingrecordwarning"></a>110 – CustomTrackingRecordWarning
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|110|  
|キーワード|UserEvents、EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|レベル|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、ワークフロー インスタンス内のアクティビティが警告レベルで CustomTrackingRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>メッセージ  
 TrackRecord = CustomTrackingRecord、InstanceID = %1、RecordNumber=%2、EventTime=%3、Name=%4、ActivityName=%5、ActivityId=%6、ActivityInstanceId=%7、ActivityTypeName=%8、Data=%9、Annotations=%10、ProfileName = %11  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|名前|xs:string|CustomTrackingRecord の名前|  
|ActivityName|xs:string|CustomTrackingRecord を出力するアクティビティの名前|  
|ActivityId|xs:string|CustomTrackingRecord を出力するアクティビティの ID|  
|ActivityInstanceId|xs:string|CustomTrackingRecord を出力するアクティビティのインスタンス|  
|ActivityTypeName|xs:string|CustomTrackingRecord を出力するアクティビティの名前|  
|データ|xs:string|このイベントで追跡されたデータ。  形式で xml 要素に値が格納されている\<項目 >\<項目名 ="dataName"type="System.String"> dataValue\<項目/>\</items >。  データが追跡されなかったかどうかは、文字列に含まれる\<項目/>。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えるかどうかは、注釈を削除して、データ値を置き換えることによって、イベントが切り捨てられる\<項目 >.\</items >。  string、char、bool、int、short、long、uint、ushort、ulong、System.Single、float、double、System.Guid、System.DateTimeOffset、および System.DateTime の各型は、ToString() から返される値として格納されます。  その他のすべての型は、System.Runtime.Serialization.NetDataContractSerializer を使用してシリアル化されます。|  
|コメント|xs:string|このイベントに追加された注釈。  形式で xml 要素に値が格納されている\<項目 >\<項目名 ="annotationName"type="System.String"> annotationValue\<項目/>\</items >。  注釈が指定されていない場合、文字列が含まれる\<項目/>。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えるかどうかは、注釈を削除しを持つ注釈の値を置き換えることによって、イベントが切り捨てられ\<項目 >.\</items >。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  これは、形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' 例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
