---
title: トレースの種類の概要
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856002"
---
# <a name="trace-type-summary"></a>トレースの種類の概要
[ソースレベル](https://go.microsoft.com/fwlink/?LinkID=94943)では、さまざまなトレースレベルを定義します。重大、エラー、警告、情報、および詳細に加えて、トレース境界とアクティビティ`ActivityTracing`転送イベントの出力を切り替えるフラグについて説明します。  
  
 また、から<xref:System.Diagnostics>出力できるトレースの種類に対して[traceeventtype](https://go.microsoft.com/fwlink/?LinkId=95169)を確認することもできます。  
  
 最も重要な種類を次の表に示します。  
  
|トレースの種類|説明|  
|----------------|-----------------|  
|重大|致命的なエラーまたはアプリケーションのクラッシュ。|  
|Error|回復可能なエラー。|  
|警告|情報メッセージ。|  
|[情報]|重大ではない問題。|  
|Verbose|トレースのデバッグ。|  
|開始|処理の論理単位の開始。|  
|[中断]|処理の論理単位の中断。|  
|Resume|処理の論理単位の再開。|  
|停止|処理の論理単位の停止。|  
|転送|相関 ID の変更。|  
  
 アクティビティは、上記のトレースの種類の組み合わせとして定義されます。  
  
 ローカル (トレース ソース) スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 これは、アクティビティが次の条件を満たす必要があることを意味します。  
  
- アクティビティは、Start トレースによって開始し、Stop トレースによって停止する必要があります。  
  
- Suspend トレースまたは Resume トレースの直前に Transfer トレースが必要です。  
  
- Suspend トレースと Resume トレースが存在する場合、これらのトレースの間にトレースが存在することはできません。  
  
- 上記の条件を満たしている限り、Critical/Error/Warning/Information/Verbose/Transfer の各トレースはいくつでも含めることができます。  
  
 グローバル スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。  
  
`R+`  
  
 R はローカル スコープのアクティビティを表す正規表現です。 これは、次のようになります。  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
