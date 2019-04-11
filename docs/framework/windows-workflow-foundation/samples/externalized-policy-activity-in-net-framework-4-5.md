---
title: .NET Framework 4.5 の外部化されたポリシー アクティビティ
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: 622b0f14281d5b068700d9e4fe03485aa1a60fcb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338281"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>.NET Framework 4.5 の外部化されたポリシー アクティビティ

このサンプルでは、ExternalizedPolicy4 アクティビティを使用して既存の実行方法について[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]Windows Workflow Foundation (WF 3.5)<xref:System.Workflow.Activities.Rules.RuleSet>オブジェクト[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]ルール エンジンを使用して直接 Windows Workflow Foundation (WF 4.5)WF 3.5 に付属しています。 このアクティビティを使用すると、既存の WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> を開いて実行できます。 Windows Workflow Foundation の一部として含まれている WF 3.5 ルール エンジンの詳細については、「 [Windows Workflow Foundation ルール エンジンの概要](https://go.microsoft.com/fwlink/?LinkId=166079)します。 移行の詳細については規則を[!INCLUDE[wf1](../../../../includes/wf1-md.md)]で[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]、移行のガイダンスをお読みください[移行ガイダンス](../migration-guidance.md)します。

## <a name="projects-in-this-sample"></a>このサンプルのプロジェクト

|プロジェクト名|説明|メイン ファイル|
|-|-|-|
|ExternalizedPolicy4|ExternalizedPolicy4 アクティビティとその WF 4.5 デザイナーが含まれます。|**ExternalizedPolicy4.cs**: アクティビティ定義。<br /><br /> **ExternalizedPolicy4Designer.xaml**:ExternalizedPolicy4 アクティビティのカスタム デザイナー。 WF 3.5 ルール エンジンからルール エディター (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) を使用します。|
|ImperativeCodeClientSample|命令型 C# コードで、ExternalizedPolicy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです (デザイナーは不使用)。|**ApplyDiscount.rules**:ファイルと[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ルール定義。<br /><br /> **Order.cs**:顧客の注文を表す型です。 ルールはこの型のオブジェクトに適用されます。<br /><br /> **Program.cs**:構成および Order オブジェクトのインスタンスに ApplyDiscount.rules で定義されたルールを適用する Policy4 アクティビティを含むワークフローを実行します。<br /><br /> App.config:ルール ファイルのパスを持つ構成ファイル。|
|DesignerClientSample|[!INCLUDE[wf1](../../../../includes/wf1-md.md)] デザイナーで、ExternalPolicy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです。|**Sequence1.xaml**:Policy4 アクティビティを使用してルール評価を実行するシーケンシャル ワークフローです。<br /><br /> **Program.cs**:Sequence1.xaml で定義されているワークフローのインスタンスを実行します。|

## <a name="the-externalizedpolicy4-activity"></a>ExternalizedPolicy4 アクティビティ

ExternalizedPolicy4 アクティビティは、WF 4.5 のワークフロー内で WF 3.5 <xref:System.Activities.NativeActivity> オブジェクトを実行できるようにする <xref:System.Workflow.Activities.Rules.RuleSet> です。 次のコード例は、このアクティビティのパブリック オブジェクト モデルの簡略化された定義です。

```
public class ExternalizedPolicy4Activity<TResult>: CodeActivity
{
    public string RulesFilePath

    public string RuleSetName

    [RequiredArgument]
    public InArgument<T> TargetObject

    [RequiredArgument]
    public OutArgument<T> ResultObject

    public OutArgument<ValidationErrorCollection> ValidationErrors
}
```

|プロパティ|説明|
|-|-|
|RuleSetFilePath|アクティビティが実行されるときに評価される .NET Framework 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> ファイルのパスです。|
|RuleSetName|.rules ファイル内で使用される <xref:System.Workflow.Activities.Rules.RuleSet> の名前です。|
|TargetObject|<xref:System.Workflow.Activities.Rules.Rule> の <xref:System.Workflow.Activities.Rules.RuleSet> オブジェクトを評価する対象のオブジェクトです。|
|ResultObject|ルールが適用された後の結果として得られるオブジェクトです (たとえば、ルールが Input 引数に対して適用され、結果が Result 引数に格納されます)。|
|ValidationError|実行前に対象オブジェクトに対して <xref:System.Workflow.Activities.Rules.RuleSet> を検証するときに、WF 3.5 ルール エンジンから返される検証エラーのリストです。|

## <a name="externalizedpolicy4-activity-designer"></a>ExternalizedPolicy4 アクティビティ デザイナー

ExternalizedPolicy4 デザイナーを使用すると、コードを記述せずに、既存の RuleSet を使用するようにアクティビティを構成できます。 .rules ファイルのパスを設定し、使用する <xref:System.Workflow.Activities.Rules.RuleSet> の名前を指定するだけです。 また、<xref:System.Workflow.Activities.Rules.RuleSet> を変更することもできます。 ソリューションをビルドすると、Microsoft.Samples.Activities.Rules セクションのツールボックス内からこのデザイナーを使用できるようになります。 このデザイナーでは、.rules ファイルと <xref:System.Workflow.Activities.Rules.RuleSet> を選択できます。 ときに、 **Edit RuleSet**ボタンがクリックされた、WF 3.5<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>が表示されます。 このダイアログはホストを変更した WF 3.5 ルール エディターであり、ExternalizedPolicy4 アクティビティで実行するルールを表示および編集するために使用します。

## <a name="policy4-and-externalpolicy4"></a>Policy4 と ExternalPolicy4

ポリシー アクティビティを作成して、WF 4.5 ワークフローでの .NET Framework 3.5 RuleSet を実行できます。 <xref:System.Workflow.Activities.Rules.RuleSet> は、Policy4 アクティビティの XAML 定義でインラインでシリアル化されます。 ExternalizedPolicy4 サンプルでは、既存の外部 <xref:System.Workflow.Activities.Rules.RuleSet> (.rules ファイル内に格納) を使用する方法を示します。

## <a name="use-this-sample"></a>このサンプルを使用します。

このサンプルを実行するのに特別な設定は必要ありません。 Visual Studio でソリューションを開き、キーを押します**F5**アプリケーションを実行します。

このサンプルには、2 つのクライアント アプリケーションが含まれています。ImperativeCodeClientSample と DesignerClientSample します。 ImperativeCodeClientSample クライアントは、C# 命令型コードを使用して ExternalizedPolicy4 アクティビティを構成および実行する方法を示します。 DesignerClientSample は、デザイナーを使用して ExternalizedPolicy4 アクティビティを構成および実行する方法を示します。

### <a name="run-the-imperativecodeclientsample-application"></a>ImperativeCodeClientSample アプリケーションを実行します。

1. Visual Studio を使用してを開く、 *Policy4sample.sln*ソリューション ファイル。

2. **ソリューション エクスプ ローラー**を右クリックし、 **ImperativeCodeClientSample**プロジェクト選び**スタートアップ プロジェクトとして設定**します。

3. プロジェクトを実行するには、キーを押して**Ctrl**+**f5 キーを押して**します。

### <a name="run-the-designerclientsample-application"></a>DesignerClientSample アプリケーションを実行します。

1. Visual Studio を使用してを開く、 *Policy4sample.sln*ソリューション ファイル。

2. **ソリューション エクスプ ローラー**を右クリックし、 **DesignerClientSample**プロジェクト選び**スタートアップ プロジェクトとして設定**します。

3. キーを押して**Ctrl**+**Shift**+**B**プロジェクトをコンパイルします。

4. キーを押して**Ctrl**+**F5**プロジェクトを実行します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。
>
> このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
