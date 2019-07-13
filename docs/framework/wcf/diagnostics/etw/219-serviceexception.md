---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781733"
---
# <a name="219---serviceexception"></a>219 - ServiceException
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|219|  
|キーワード|EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel|  
|レベル|Error|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、WCF サービスがハンドルされない例外を検出した場合に生成されます。 これには、アクティベーション中のハンドルされない例外、メッセージ処理中のハンドルされない例外、およびユーザー コード内でのハンドルされない例外が含まれます。  
  
## <a name="message"></a>メッセージ  
 メッセージの処理中に種類 '%2' のハンドルされない例外がスローされました。 完全な例外 ToString: %1。  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|CLR 例外に対して `ToString`() を呼び出した結果。|  
|ExceptionTypeName|`xs:string`|例外の型の CLR FullName。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 その形式が定義されている ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName'。 例:' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
