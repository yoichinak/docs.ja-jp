---
title: Pick アクティビティの使用
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 0b2fbeb9b32406dd913d7e1ee87ac167113d0f28
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302981"
---
# <a name="using-the-pick-activity"></a>Pick アクティビティの使用
このサンプルでは、<xref:System.Activities.Statements.Pick> アクティビティを使用する方法を示します。

 <xref:System.Activities.Statements.Pick> アクティビティでは、イベント ベースの制御モデリングを提供します。 このアクティビティの動作は C# の `switch` ステートメントに似ています。`switch` ステートメントでは、その分岐のうち 1 つだけが実行されます。 ただし、値に基づいて分岐が実行される `switch` ステートメントと異なり、<xref:System.Activities.Statements.Pick> アクティビティでは、アクティビティの完了の状態に基づいて分岐を実行します。

 このサンプルでは、指定した時間内にコンソールでユーザー名を入力するようユーザーに求めます。 このサンプルの <xref:System.Activities.Statements.Pick> アクティビティには、ユーザーが 5 秒以内にユーザー名を入力したかどうかに基づいて実行される 2 つの分岐があります。 ユーザーが 5 秒以内にユーザー名を入力した場合は、カスタムの `ReadLine` アクティビティを含む最初の分岐が実行されます。それ以外の場合は、<xref:System.Activities.Statements.Delay> アクティビティを含むもう 1 つの分岐が実行されます。 コンソールでユーザー名を入力すると、そのユーザー名がコンソールに出力されます。 5 秒以内に入力しないと、操作はタイムアウトします。

## <a name="demonstrates"></a>使用例
 <xref:System.Activities.Statements.Pick> アクティビティ。

## <a name="discussion"></a>説明
 このサンプルには、デザイナー ワークフローとコード化されたワークフローがあります。

 デザイナーのワークフローのデザイナー バージョンのサンプルでは、デザイナーでワークフローを作成する方法を示します。 次のファイルがあります。

-   Program.cs:含まれています、`Main`サンプル ワークフローを実行する関数。

-   Readstring.cs:コンソールからいくつかの入力を読み取るカスタム アクティビティ。

-   Sequence1.xaml:Pick を使用するデザイナーを使用して作成されたワークフローです。

 コード化されたワークフロー コード化されたバージョンのサンプルでは、デザイナーでワークフローを作成する方法を示します。 次のファイルがあります。

-   Program.cs:含まれています、`Main`サンプル ワークフローを実行する関数。

-   Readstring.cs:コンソールからいくつかの入力を読み取るカスタム アクティビティ。

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1. Visual Studio 2010 を使用して、Pick.sln ソリューション ファイルを開きます。

2. ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。

3. ソリューションを実行するには、F5 キーを押します。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`