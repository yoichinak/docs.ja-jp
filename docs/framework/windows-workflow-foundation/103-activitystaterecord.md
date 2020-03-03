---
title: 103 - ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 38cec570cffebf6af6d35df481cbec8c7dca8cd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924385"
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|103|  
|キーワード|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、ワークフロー インスタンス内のアクティビティが ActivityStateRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>メッセージ  
 TrackRecord = ActivityStateRecord、InstanceID = %1、RecordNumber=%2、EventTime=%3、State = %4、Name=%5、ActivityId=%6、ActivityInstanceId=%7、ActivityTypeName=%8、Arguments=%9、Variables=%10、Annotations=%11、ProfileName = %12  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|状態|xs:string|アクティビティの状態|  
|名前|xs:string|イベントを生成したアクティビティの表示名|  
|ActivityId|xs:string|生成したアクティビティのアクティビティ ID|  
|ActivityInstanceId|xs:string|生成したアクティビティのアクティビティ インスタンス ID|  
|ActivityTypeName|xs:string|生成したアクティビティの型名|  
|引数|xs:string|このイベントで追跡された引数。  形式で xml 要素に値が格納されている\<項目 >\<項目名 ="argumentName"type="System.String"> argumentValue\<項目/>\</items >。  引数が追跡されなかったかどうかは、文字列が含まれる\<項目/>。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えるかどうかは、イベントは、注釈が破棄して、注釈の値がの交換によって切り捨てられる\<項目 >.\</items >。  string、char、bool、int、short、long、uint、ushort、ulong、System.Single、float、double、System.Guid、System.DateTimeOffset、および System.DateTime の各型は、ToString() から返される値として格納されます。  その他のすべての型は、System.Runtime.Serialization.NetDataContractSerializer を使用してシリアル化されます。|  
|変数|xs:string|このイベントで追跡された変数。  形式で xml 要素に値が格納されている\<項目 >\<項目名 ="variableName"type="System.String"> variableValue\<項目/>\</items >。  変数が追跡されなかったかどうかは、文字列が含まれる\<項目/>。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えるかどうかは、イベントは、注釈を削除して、変数値がの交換によって切り捨てられる\<項目 >.\</items >。  string、char、bool、int、short、long、uint、ushort、ulong、System.Single、float、double、System.Guid、System.DateTimeOffset、および System.DateTime の各型は、ToString() から返される値として格納されます。  その他のすべての型は、System.Runtime.Serialization.NetDataContractSerializer を使用してシリアル化されます。|  
|コメント|xs:string|このイベントに追加された注釈。  形式で xml 要素に値が格納されている\<項目 >\<項目名 ="annotationName"type="System.String"> annotationValue\<項目/>\</items >。  注釈が指定されていない場合、文字列が含まれています\<項目/>。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えるかどうかは、イベントは、注釈が破棄して、注釈の値がの交換によって切り捨てられる\<項目 >.\</items >。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  その形式が定義されている ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' の使用例。' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
