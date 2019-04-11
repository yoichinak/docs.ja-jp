---
title: Windows フォームでの電源管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 6bb9b4f30a88ece93b17ff2510087b220d538738
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154675"
---
# <a name="power-management-in-windows-forms"></a>Windows フォームでの電源管理
Windows フォーム アプリケーションによっては、Windows オペレーティング システムの電源管理機能を活用がかかります。 アプリケーションでは、コンピューターの電源の状態を監視でき、状態の変更が発生したときにアクションを実行することができます。 など、アプリケーションがポータブル コンピューターで実行している場合、コンピューターのバッテリ残量が一定のレベルを下回ったときに、アプリケーションで特定の機能を無効にします。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供、 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> AC 電源の状態またはバッテリの状態が変更されたときや、ユーザーが中断またはオペレーティング システムが再開されるなどの電源ステータスの変更があるたびに発生するイベントです。 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>のプロパティ、<xref:System.Windows.Forms.SystemInformation>クラスにすることが次のコード例に示すように現在の状態では、クエリに使用されます。  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 それに、<xref:System.Windows.Forms.BatteryChargeStatus>列挙型、<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>プロパティには、バッテリ容量を決定するための列挙体も含まれています (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) とバッテリの充電の割合 (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>、 <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>)。  
  
 使用することができます、<xref:System.Windows.Forms.Application.SetSuspendState%2A>のメソッド、<xref:System.Windows.Forms.Application>コンピューターを休止状態または中断モードにします。 場合、`force`に設定されている引数`false`、オペレーティング システムが中断するためのアクセス許可を要求するすべてのアプリケーションにイベントをブロードキャストします。 場合、`disableWakeEvent`に設定されている引数`true`、オペレーティング システムがスリープ解除のすべてのイベントを無効にします。  
  
 次のコード例では、コンピュータを休止状態にする方法を示します。  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
