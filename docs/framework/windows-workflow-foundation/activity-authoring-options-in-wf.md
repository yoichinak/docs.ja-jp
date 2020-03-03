---
title: WF のアクティビティ作成オプション
ms.date: 03/30/2017
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
ms.openlocfilehash: 219d759cd1390a83abfb90af509b21047085f6e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774232"
---
# <a name="activity-authoring-options-in-wf"></a>WF のアクティビティ作成オプション
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、カスタム アクティビティを作成するオプションがいくつか用意されています。 特定のアクティビティを作成するために使用する適切な方法は、実行時に必要な機能によって異なります。  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>カスタム アクティビティを作成するために使用する基本アクティビティ クラスの決定  
 次の表は、カスタム アクティビティの基本クラスに使用できる機能の一覧です。  
  
|基本アクティビティ クラス|使用できる機能|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|システム標準アクティビティおよびカスタム アクティビティのグループを複合アクティビティに構成します。|  
|<xref:System.Activities.CodeActivity>|オーバーライドできる <xref:System.Activities.CodeActivity%601.Execute%2A> メソッドを提供することで、命令型機能を実装します。 また、追跡、変数、および引数へのアクセスを提供します。|  
|<xref:System.Activities.NativeActivity>|<xref:System.Activities.CodeActivity> のすべての機能を提供します。さらに、アクティビティの実行中止、子アクティビティの実行の取り消し、ブックマークの使用、および、アクティビティ、アクティビティのアクション、および機能のスケジュールも提供します。|  
|<xref:System.Activities.DynamicActivity>|WF デザイナーおよび <xref:System.ComponentModel.ICustomTypeDescriptor> を介したランタイム機構と連携するアクティビティの構築に対応する、DOM のようなアプローチを提供します。これにより、新しい型を定義せずに新しいアクティビティを作成できるようになります。|  
  
## <a name="authoring-activities-using-activity"></a>アクティビティを使用したアクティビティの作成  
 <xref:System.Activities.Activity> から派生するアクティビティは、他の既存のアクティビティをまとめることで機能を構成します。 これらのアクティビティには、既存のカスタム アクティビティと、[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] アクティビティ ライブラリのアクティビティを使用できます。 これらのアクティビティをまとめることは、カスタム機能を作成するための最も基本的な方法です。 このアプローチは、ワークフローを作成するうえでビジュアル デザイン環境を使用するときによく採用されます。  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>CodeActivity または AsyncCodeActivity を使用したアクティビティの作成  
 <xref:System.Activities.CodeActivity> または <xref:System.Activities.AsyncCodeActivity> から派生するアクティビティは、<xref:System.Activities.CodeActivity%601.Execute%2A> メソッドをカスタムの命令型コードでオーバーライドすることで、命令型機能を実装できます。 カスタム コードが実行されるのは、アクティビティが実行時に実行されるときです。 この方法で作成されたアクティビティはカスタム機能にアクセスできますが、実行時環境へのフル アクセス、子アクティビティのスケジュール機能、ブックマークの作成、Cancel メソッドや Abort メソッドのサポートなどの、ランタイムのすべての機能にアクセスすることはできません。 <xref:System.Activities.CodeActivity> を実行すると、(<xref:System.Activities.CodeActivityContext> クラスまたは <xref:System.Activities.AsyncCodeActivityContext> クラスを介して) 限定されたバージョンの実行時環境にアクセスできます。 <xref:System.Activities.CodeActivity> を使用して作成したアクティビティは、引数と変数の解決、拡張、および追跡にアクセスできます。 非同期アクティビティのスケジュールは、<xref:System.Activities.AsyncCodeActivity> を使用して実行できます。  
  
## <a name="authoring-activities-using-nativeactivity"></a>NativeActivity を使用したアクティビティの作成  
 <xref:System.Activities.NativeActivity> から派生するアクティビティは、<xref:System.Activities.CodeActivity> から派生するアクティビティと同様に、<xref:System.Activities.NativeActivity.Execute%2A> をオーバーライドすることで、命令型機能を作成します。ただし、<xref:System.Activities.NativeActivityContext> メソッドに渡される <xref:System.Activities.NativeActivity.Execute%2A> を介して、ワークフロー ランタイムのすべての機能にもアクセスできます。 このコンテキストは、子アクティビティのスケジュールと取り消し、<xref:System.Activities.ActivityAction> および <xref:System.Activities.ActivityFunc%601> オブジェクトの実行、ワークフローへのトランザクションの流し込み、非同期プロセスの呼び出し、実行の取り消しと中止、実行プロパティおよび実行拡張機能へのアクセス、およびブックマーク (一時停止したワークフローの再開を処理) をサポートします。  
  
## <a name="authoring-activities-using-dynamicactivity"></a>DynamicActivity を使用したアクティビティの作成  
 他の 3 種類のアクティビティとは異なり、<xref:System.Activities.DynamicActivity> から新しい型を派生することでは新しい機能は作成されません (クラスはシールされています)。その代わり、アクティビティのドキュメント オブジェクト モデル (DOM) を使用して、<xref:System.Activities.DynamicActivity.Properties%2A> プロパティと <xref:System.Activities.DynamicActivity.Implementation%2A> プロパティに機能をまとめることで、新しい機能を作成します。  
  
## <a name="authoring-activities-that-return-a-result"></a>結果を返すアクティビティの作成  
 多くのアクティビティは、実行後に結果を返します。 この目的でアクティビティにカスタムの <xref:System.Activities.OutArgument%601> を定義することは常に可能ですが、代わりに <xref:System.Activities.Activity%601> を使用するか、<xref:System.Activities.CodeActivity%601> または <xref:System.Activities.NativeActivity%601> から派生することをお勧めします。 これらの各基本クラスには、アクティビティの戻り値に使用できる Result という <xref:System.Activities.OutArgument%601> があります。 結果を返すアクティビティは、1 つの結果のみをアクティビティから返す必要がある場合にのみ使用します。複数の結果を返す必要がある場合は、別の <xref:System.Activities.OutArgument%601> メンバーを代わりに使用します。
