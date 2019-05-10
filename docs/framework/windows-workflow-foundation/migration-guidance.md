---
title: 移行のガイドライン
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 64f71061dda96279a7aa0fffa3642ae6d2d01c8f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649383"
---
# <a name="migration-guidance"></a>移行のガイドライン
[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]Microsoft は 2 つ目のメジャー バージョンの Windows Workflow Foundation (WF) をリリースします。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] は、[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (これに含まれていた System.Workflow.* 名前空間の型は現在 WF3 と呼ばれています) でリリースされ、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] で強化されました。 WF3 はまたの一部、[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]が新しいワークフロー テクノロジがありますが存在します (System.Activities。 内の型\*名前空間。 WF4 と呼ばれます)。 WF4 の導入時期を検討する場合は、最初にそのタイミングの管理を認識することが重要です。  
  
- WF3 は [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] で完全にサポートされています。  
  
- WF3 のアプリケーションは、変更しなくても [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] で実行され、引き続き完全にサポートされます。  
  
- 新しい WF3 アプリケーションを作成して、既存のアプリケーションが Visual Studio 2012 で編集できるし、は完全にサポートします。  
  
 .NET Framework 4 を採用する意思決定を WF4 に移行する決定から分離するために、(System.Activities.*) WF3 から (System.Workflow。\*)。 このトピックでは、WF の移行のガイドラインへのリンクを提供し、WF3 および WF4 での作業に関する情報を提供します。  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>WF の移行に関するホワイト ペーパーとクックブック  
 [WF の移行の概要](https://go.microsoft.com/fwlink/?LinkId=153873)関係 WF3 と WF4 と移行方法の大まかな概要を説明します。 関連トピックでは、特定のトピックを掘り下げて説明します。  
  
 [WF 移行の概要](https://go.microsoft.com/fwlink/?LinkId=153873)  
 WF3 と WF4 の関係、および .NET 4 のワークフロー テクノロジのユーザーまたは潜在的なユーザーとして使用できる選択肢について説明します。  
  
 [WF の移行:WF3 を開発のベスト プラクティス](https://go.microsoft.com/fwlink/?LinkId=153852)  
 より簡単に WF4 に移行できるように、WF3 の成果物を設計する方法について説明します。  
  
 [WF のガイダンス:ルール](https://go.microsoft.com/fwlink/?LinkId=153854)  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] のソリューションに規則関連の投資を促進する方法について説明します。  
  
 [WF のガイダンス:ステート マシン](https://go.microsoft.com/fwlink/?LinkId=153855)  
 ステート マシンのアクティビティがない場合の WF4 の制御フロー モデリングについて説明します。  
  
 このガイダンスは、.NET Framework 4 を対象とするワークフロー プロジェクトにのみ該当することに注意してください。 ステート マシンのワークフローは、Platform Update 1 のリリースで .NET 4.0.1 に追加され、.NET Framework 4.5 の一部として含まれていました。 .NET 4.0.1 ~ 4.0.3 および .NET Framework 4.5 のステート マシン ワークフローの詳細については、次を参照してください。 [Microsoft .NET Framework 4 の機能の更新プログラム 4.0.1](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100))と[ステート マシン ワークフロー](state-machine-workflows.md)します。  
  
 [WF 移行のクックブック:カスタム アクティビティ](https://go.microsoft.com/fwlink/?LinkId=153856)  
 WF3 のカスタム アクティビティを WF4 で再設計する場合のサンプルと手順について説明します。  
  
 [WF 移行のクックブック:高度なカスタム アクティビティ](https://go.microsoft.com/fwlink/?LinkId=275560)  
 WF3 キューを使用して子アクティビティを WF4 カスタム アクティビティとしてスケジュールする高度な WF3 カスタム アクティビティを再設計するための指針を示します。  
  
 [WF 移行のクックブック:ワークフロー](https://go.microsoft.com/fwlink/?LinkId=153858)  
 WF3 のワークフローを WF4 で再設計する場合のサンプルと手順について説明します。  
  
 [WF 移行のクックブック:ワークフローのホスティング](https://go.microsoft.com/fwlink/?LinkId=275561)  
 WF3 ホスティング コードを WF4 ホスティング コードとして再設計するための指針を示します。 この目的は、WF3 と WF4 のワークフロー ホスティングの主な違いを説明することです。  
  
 [WF 移行のクックブック:ワークフロー追跡](https://go.microsoft.com/fwlink/?LinkId=275562)  
 WF3 追跡コードを再設計するための指針と、同等の WF4 追跡コードと構成を使用した構成を示します。  
  
 [WF のガイダンス:ワークフロー サービス](https://go.microsoft.com/fwlink/?LinkId=275564)  
 事前定義アクティビティの一般的なシナリオ向けに、WF3 で作成した Windows Communication Foundation (WCF) Web サービス (一般にワークフロー サービスと呼ばれます) を実装するワークフローを WF4 を使用するように再設計するための詳細な手順を例を中心として示します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Activities.Statements.Interop>
