---
title: Windows Workflow Foundation で非推奨の型
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: d41bf147cd079a3d6d3714da5595732de3dcb7de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774050"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation で非推奨の型
.NET 4 の段階で、ワークフロー チームは、<xref:System.Activities> 名前空間のまったく新しいワークフロー エンジンをリリースしました。 ほとんどの"WF 3"で型をマークする .NET 4.5 ベータ版のリリースでは<xref:System.Workflow.Activities>、 <xref:System.Workflow.ComponentModel>、および<xref:System.Workflow.Runtime>不使用と名前空間。  
  
## <a name="obsolete-namespaces-and-tools"></a>旧式の名前空間とツール  
 次のアセンブリには、今後非推奨とされるパブリック型が 1 つ以上含まれています：  
  
- System.Workflow.Activities.dll  
  
- System.Workflow.ComponentModel.dll  
  
- System.Workflow.Runtime.dll  
  
- System.WorkflowServices.dll  
  
- Microsoft.Workflow.DebugController.dll  
  
- Microsoft.Workflow.Compiler.exe  
  
- Wfc.exe  
  
 その結果、非推奨とされた WF 3 API を今後使用すると、ビルド時に警告が発生し、次のようなメッセージが表示されます：  
  
 **警告 bc 40000:X は廃止されています。WF 3 の型が非推奨とされます。代わりに WF 4 を使用してください。** WF 3 の型は .NET Framework の将来のリリースで削除されますが、実際の削除時期はまだ未定です (4.5 では行われません)。 この段階的な変更は、今後の方向性を示し、お客様が WF 4 モデルに余裕をもって移行するための期間を確保するためのものです。 WF 3 の型をサポートするためにいく予定、もちろん、[マイクロソフト サポート ライフ サイクル ポリシー](https://aka.ms/MicrosoftSupportLifecycle)します。 既存の WF3 のアプリケーションでは、.NET 4.5 では、上で問題なく実行され、Visual Studio 2012 が新規および既存の wf 3 ベースのソリューションをサポートします。  
  
 <xref:System.Workflow.Activities.Rules> 名前空間に含まれるルール関連の型については、WF 4.5 には相当する型がないため、非推奨扱いにはなりません。  
  
 WF 4 へのアプリケーション移行を希望お客様は、のヘルプを検索は、[ワークフロー 4 移行ガイダンス](migration-guidance.md)します。
