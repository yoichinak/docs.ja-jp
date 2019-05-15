---
title: 制限された並列 ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 2694173e203fae9b620e9594d6d4a494bdedafef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637769"
---
# <a name="throttled-parallel-foreach"></a>制限された並列 ForEach

`ThrottleParallelForEach` アクティビティは、実行する同時分岐の数を制限するためのコンカレンシー要因を設定できるという 1 つの例外を除き、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティと似ていることについて示します。 `ThrottleParallelForEach` アクティビティは、<xref:System.Activities.NativeActivity> クラスを介してのみアクセスできる他のアクティビティ (子アクティビティ) をスケジュールする必要があるため、<xref:System.Activities.NativeActivityContext> クラスから派生します。

## <a name="projects"></a>プロジェクト

|**ProjectName**|**説明**|**メイン ファイル**|
|-|-|-|
|ThrottledParallelForEach|`ThrottledParallelForEach` アクティビティとそのデザイナーが含まれます。|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach` アクティビティ定義。|
|CodeTestClient|命令型コードを使用して、`ThrottledParallelForEach` を含むワークフローを構成および実行するサンプル クライアント アプリケーション。|Program.cs<br /><br /> サンプル ワークフローのインスタンスを定義および実行します。|

## <a name="to-use-this-sample"></a>このサンプルを使用するには

1. Visual Studio 2010 を使用して、ThrottledParallelForEach.sln ファイルを開きます。

2. ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。

3. ソリューションを実行するには、F5 キーを押します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
