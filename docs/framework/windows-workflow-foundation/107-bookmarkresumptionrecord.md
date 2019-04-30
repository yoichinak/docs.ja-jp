---
title: 107 -- BookmarkResumptionRecord
ms.date: 03/30/2017
ms.assetid: aa2d37ed-2bfa-439b-89e8-a9354027f155
ms.openlocfilehash: 860ed7cc065a862d100b0a8c6a88458e61930b9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052847"
---
# <a name="107----bookmarkresumptionrecord"></a>107 -- BookmarkResumptionRecord
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|107|  
|キーワード|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、ワークフロー インスタンスが BookmarkResumptionRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>メッセージ  
 TrackRecord = BookmarkResumptionRecord、InstanceID=%1、RecordNumber=%2,EventTime=%3、Name=%4、SubInstanceID=%5、OwnerActivityName=%6、OwnerActivityId =%7、OwnerActivityInstanceId=%8、OwnerActivityTypeName=%9、Annotations=%10、ProfileName = %11  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|名前|xs:string|再開したブックマークの名前|  
|SubInstanceID|xs:GUID|ブックマーク スコープの ID|  
|OwnerActivityName|xs:string|ブックマーク アクティビティの名前|  
|OwnerActivityId|xs:string|ブックマーク アクティビティの ID|  
|OwnerActivityInstanceId|xs:string|ブックマーク アクティビティのインスタンス ID|  
|OwnerActivityTypeName|xs:string|ブックマーク アクティビティの型|  
|コメント|xs:string|このイベントに追加された注釈。  形式で xml 要素に値が格納されている\<項目 >\<項目名 ="annotationName"type="System.String"> annotationValue\<項目/>\</items >。  注釈が指定されていない場合、文字列が含まれています\<項目/>。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えるかどうかは、イベントは、注釈が破棄して、注釈の値がの交換によって切り捨てられる\<項目 >.\</items >。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  その形式が定義されている ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' の使用例。' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
