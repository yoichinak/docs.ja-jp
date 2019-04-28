---
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 6eb80d6f0b20af9aae6e7de5248323088e352b26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596480"
---
# <a name="301---userdefinederroroccurred"></a>301 - UserDefinedErrorOccurred
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|301|  
|キーワード|Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring|  
|レベル|Error|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、ユーザー コードから生成されます。 開発者は、カスタム定義のエラー イベントがサービスで発生したときに、このイベントを生成できます。 これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。 また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。  
  
## <a name="message"></a>メッセージ  
 名前:'%1'、参照:'%2'、ペイロード:%3  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|名前|`xs:string`|イベントのユーザー定義名。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 その形式が定義されている ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName'。 例:' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。|  
|Payload|`xs:string`|イベントのユーザー定義ペイロード。|
