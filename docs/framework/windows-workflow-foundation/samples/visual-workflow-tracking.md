---
title: ビジュアル ワークフロー追跡
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 6e87b0ef5a0d6fa97c87c99a63fe0e23c389140c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004714"
---
# <a name="visual-workflow-tracking"></a>ビジュアル ワークフロー追跡
このサンプルでは、[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] のデバッグ機能を使用してビジュアル ワークフロー追跡アプリケーションを作成する方法を示します。

## <a name="sample-details"></a>サンプルの詳細
 このアプリケーションは、Workflow.xaml に定義されている単純なフローチャート ワークフローを実行し、ワークフロー デザイナーを再ホストして現在実行中のワークフローを表示します。 ワークフローが実行されると、現在実行中のアクティビティが黄色の枠とデバッグ矢印で示されます。 さらに、ワークフローによって生成された追跡レコードもアプリケーション ウィンドウに表示されます。 ワークフロー追跡の詳細については、次を参照してください。[ワークフロー追跡とトレース](../workflow-tracking-and-tracing.md)します。 ワークフロー デザイナーの再ホストの詳細については、次を参照してください。[ワークフロー デザイナーのホスト変更](../rehosting-the-workflow-designer.md)します。

 このワークフロー シミュレーターは、2 つのディクショナリを保持することによって機能します。 一方のディクショナリには、現在実行中のアクティビティ オブジェクトと、そのアクティビティがインスタンス化された XAML の行番号とのマッピングが含まれています。 もう一方のディクショナリには、アクティビティ インスタンス ID とアクティビティ オブジェクトとのマッピングが含まれています。 カスタム追跡プロファイルを使用して追跡レコードが出力されるときには、現在実行中のアクティビティのインスタンス ID が特定されて、そのアクティビティをインスタンス化した XAML ファイルにマップされます。 その後、再ホストされたワークフロー デザイナーで、ワークフロー デバッガーと同じ方法を使用してそのアクティビティがデザイナー画面で強調表示されます (アクティビティが黄色の枠で囲まれ、デザイナーの左端に黄色の矢印が表示されます)。

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1. Visual Studio 2010 でサンプル ディレクトリからある WorkflowSimulator.sln ファイルを開きます。

2. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。

3. Ctrl キーを押しながら F5 キーを押してサンプルを実行します。 再ホストされたワークフロー デザイナーのウィンドウに Workflow.xaml ファイルが表示されます。

4. をクリックして、**ファイル**メニュー選択し、**ワークフローを実行しています.**.

5. 現在実行中のアクティビティが上述のように強調表示され、アプリケーション ウィンドウの右側に追跡レコードが表示されます。

6. ワークフローが完了したら、任意の追跡レコードをクリックして、どのアクティビティに対応しているのかを調べることができます。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`