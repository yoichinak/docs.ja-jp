---
title: WF 内のエラー処理アクティビティ
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 410c481745cc62a55a2b6e840d82b01fcc7f5766
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707678"
---
# <a name="error-handling-activities-in-wf"></a>WF 内のエラー処理アクティビティ
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、エラーの処理および回復を実装するためのシステム標準のアクティビティが用意されています。 詳細については、「 [例外](exceptions.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。  
  
## <a name="error-handling-activities"></a>エラー処理アクティビティ  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|`TryCatch` アクティビティ内からスローされた最後の例外を再スローします。|  
|<xref:System.Activities.Statements.Throw>|例外をスローします。|  
|<xref:System.Activities.Statements.TryCatch>|例外処理を実装します。|
